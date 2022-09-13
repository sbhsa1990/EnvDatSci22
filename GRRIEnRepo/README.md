# GRRIEn repository

GRRIEn analysis stands for 

* Generalizable:
* Reproducible:
* Robust
* Interpreted

And represents a community standard for rigorous application of supervised learning to global earth observations to earth systems analysis.

More info on the GRRIEn method can be found at this [preprint](https://www.essoar.org/doi/abs/10.1002/essoar.10509942.1). A full manuscript on the GRRIEn method is currently under review.

This repository structure is meant to serve as a template for setting up a GRRIEn analysis pathway.


## Structure of the GRRIEn repository

The GRRIEn repository contains standard elements used commonly in open geospatial research to ensure maximum portability and effortless reproducibility and adaptability of supervised learning workflows utilizing global earth observations on public geodatabases. A GRRIEn repository should contain the following: 

1) Raw data (folder): contains your in-situ data, or labels, and standard delimiters of your AOI and POI (such as a start and end date, bounding box coordinates, or a shapefile). 

2) Analysis data (folder): contains the analysis-ready dataset merging your in-situ data and global proxy variables; most often a dataframe, matrix, or array. 

3) Model outputs (folder): contains trained model objects.  

4) Figures and tables (folder): contains graphical and tabular representations of results. 

5) README (html or Markdown file): providing detailed instructions on how to use elements of the repository for end-to-end analysis, the hardware and software required, the process for submitting merge requests, and license 

6) Debian Linux-compatible software image (file): A container image is a static file that includes executable code that will initiate an instance in the local compute environment containing all version-controlled software, system libraries, and system tools to execute all code in a repository. 

7) Version history (.gitconfig file) a detailed record of all edits and contributions made by individual team members to the repository over the life of the project. 

8) Code (folder): this contains all scripts used to interact with the other files and elements in the repository. Specifically, it should include: 

a) Setup.sh: bash script that initiates software image, installing all version-controlled software, libraries, and packages required by repository scripts, and creates a temporary data folder (temp data) on users machine. Reads from “Debian-Linux compatible software image,” exports to User’s machine 

b) Data source: utilizes online geodatabase API to programmatically access data for AOI and POI given catalog search parameters. Reads from: “raw data” folder, internet, exports to “temp data.” 

c) Process data code: collocates raw data (predictand) and downloaded global EO data (predictor) in space and time, including CRS conversions, resampling functions, and zonal statistics functions; converts collocated data into an analysis ready format (i.e. stacked raster, numpy array, pandas dataframe, R DataFrame); preprocesses analysis ready data for model training, including any feature reduction, variable transformations, and processing of missing data; calculates global and local multicollinearity, and global and local autocorrelation of all variables. Reads from “raw data” folder, “temp data” folder; exports to: “temp data” folder, “analysis data” folder. 

d) Model train and validate code: splits data into training and testing datasets; trains statistical model; derives statistics of model accuracy, stability, and summary statistics; calculates Moran’s I, spatial variogram, and spatial plots of model residuals; and produces model explanations. Reads from “analysis data” folder; exports to “model data” folder 

e) Figure and table generating code: code required to generate figures and tables. Reads from “processed data” folder, “model data” folder; exports to “figures and tables” folder 


