# FourStar Post-Processing scripts
This GitHub includes scripts to preview, calibrate, and extract photometric FourStar Near-InfraRed (NIR) image data of possible Low-Mass X-ray Binary (LMXB) counterparts that results from the FSRED pipeline.

Author: Iris Reitsma <br />
Co-authors: Dr. Juan Hernandez Santisteban & Jari van opijnen <br />
Data for the project is obtained by: 
- Dr. Nathalie Degenaar (2013-2014)
- Aastha S. Parikh & Prof. Dr. Rudy Wijnands (2018)
- Dr. Renee Ludlam (2018)

## About the Project
This project is a thesis for the Master Physics and Astronomy with the track Astronomy and Astrophysics at the University of Amsterdam. The project was started in September 2022 and ended in August 2023. 

### Built with
* [pandas](https://pandas.pydata.org/docs/index.html) 1.3.3
* [matplotlib](https://matplotlib.org/) 3.2.2 
* [numpy](https://numpy.org/) 1.20.3
* [astropy](https://www.astropy.org/) 5.1
* [astroquery](https://astroquery.readthedocs.io/en/latest/) 0.4.6
* [aplpy](https://aplpy.github.io/) 2.1.0
* [sklearn](https://scikit-learn.org/stable/) 0.23.2
* [hdbscan](https://hdbscan.readthedocs.io/en/latest/index.html) 0.8.29
* [linmix](https://linmix.readthedocs.io/en/latest/src/linmix.html) 0.1.0.dev1
* [photutils](https://photutils.readthedocs.io/en/stable/) 1.5.0

---
## Project Structure 
Below, we list the most important scripts and files that we used in our work. 

The [`Redundant`](./Redundant) folder holds scripts that we used as drafts or that are similar to the main scripts listed above but apply, e.g., another flux range or luminosity error. In addition, the folder holds files that we used for testing the scripts. 

The [`linmix`](./linmix) folder holds the code to apply Markov-Chain Monte-Carlo analysis, for which more information can be found [here](https://linmix.readthedocs.io/en/latest/src/linmix.html). The method is developed by [Kelly (2007)](https://iopscience.iop.org/article/10.1086/519947/meta).

### Scripts
The most important scripts for obtaining magnitudes from the FourStar data are:
* [`FSRED_post_processing`](./FSRED_post_processing.ipynb): Preview, calibrate, and extract photometric FourStar image data of possible NIR counterparts within a presumed error circle indicating the LMXB position.
* [`psf`](./psf.ipynb): Applies Point Spread Function (PSF) photometry on blended sources.

Then, we used the following notebook to prepare the data for further analysis: 
* [`Data preprocessing`](<./Data preprocessing.ipynb>): Group the data and convert magnitudes/fluxes to luminosities or log-luminosities.

We created images of the data using the following notebooks:
* [`Statistics`](./Statistics.ipynb): Create preliminary overviews of, e.g., the distribution of magnitudes in the sample and the sky position of sources.
* [`histograms`](./histograms.ipynb): Create histograms of the distribution of X-ray luminosities, hydrogen column densities and orbital periods of the sources in the sample. 
* [`Plot_luminosities`](./Plot_luminosities.ipynb): Create the NIR vs X-ray luminosity plots.

The analysis was done with the following notebooks:
* [`MCMC`](./MCMC.ipynb): Apply MCMC simulations for fitting linear relations to the NIR/X-ray data.
* [`Clustering`](./Clustering.ipynb): Apply clustering algorithms to the NIR/X-ray data.

For sources for which we did not know the X-ray state, we used the following notebook if MAXI or Swift-BAT data was available: 
* [`Find_state`](./Finds_state.ipynb): Compares MAXI and Swift-BAT data to determine the X-ray state of a source. 

### Datafiles   
We stored the data processed with [`FSRED_post_processing`](./FSRED_post_processing.ipynb) manually in a Google Sheet:
* [`FSRED Mags - Final_python`](<./FSRED Mags - Final_python.csv>)

This data is prepared for further analysis using [`Data preprocessing`](./Data_preprocessing.ipynb), which outputs the following files: 
* [`preprocessed_data`](./preprocessed_data.csv): Preprocessed data for all observations. 
* [`preprocessed_data_avg`](./preprocessed_data_avg.csv): Take the average of observations of the same source on the same day and filter. This file is uses to create plots in e.g., [`Plot_luminosities`](./Plot_luminosities.ipynb).
* [`preprocessed_data_avg_30error`](./preprocessed_data_avg_30error.csv): Take the average of observations of the same source on the same day and filter and apply a 30% error on the distance/flux if these have no error. This file is used as an input for [`MCMC`](./MCMC.ipynb).

Another file that we frequently use in the scripts is 
* [`FSRED Mags - total_source_list`](<./FSRED Mags - total_sourc_list.csv>): Provides information about each source, e.g., if the compact object is a neutron star or black hole and if the source is in quiescence/outburst or the soft/hard state.

Lastly, there are the following three files: 
* [`FSRED Mags - SourceOverviewOverleaf_filled`](<./FSRED Mags - SourceOverviewOverleaf_filled.csv>): The table of sources as included in the thesis. 
* [`paper_table`](./paper_table.xlsx): The table of observations as included in the thesis. 
* [`FSRED Mags - Porb`](<./FSRED Mags - Porb.csv>): Contains orbital periods of some sources used in [`histograms`](./histograms.ipynb).

---
## Installation 
1) Make sure to have Python version 3.8.5 installed on your machine. This project used [Anaconda](https://www.anaconda.com/), which comes with Python and a lot of nice libraries, as well as a terminal and Jupyter notebook.

2) Clone this repository using the terminal:
    ```bash
    git clone https://github.com/reitsmairis/xrbs
    ```
3) Install all dependencies listed above.


## Contact

Iris Reitsma - reitsmairis@gmail.com 

LinkedIn: https://www.linkedin.com/in/iris-reitsma-269209139/ 

Project link: https://github.com/reitsmairis/xrbs 

