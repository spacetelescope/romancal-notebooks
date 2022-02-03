# romancal-notebooks

The notebooks in this repository demonstrate how to run the Roman pipeline (`romancal`), and related tasks such as creating reference files. There is an STScI Box folder that contains example data used in some of the notebooks. Instructions on downloading the files are contained in the relevant notebooks themselves.


## Basic Setup Instructions for Running `romancal` Notebooks

Before running any of the notebooks in this repository, please run the following setup instructions. These steps will ensure you have a fresh environment for `romancal` and its dependencies, as well as Calibration Reference Database System (CRDS) set up correctly to retrieve the reference files that `romancal` uses. For the following steps, you will need to use zsh or bash.

#### Step 1: Cloning the Notebook Repository

You will first need to clone this repository on your machine to work with the notebooks.

	1. cd into the directory where you would like these notebooks, they will be cloned into a subdirectory
	2. In your zsh/bash shell, enter 'git clone https://github.com/spacetelescope/romancal-notebooks'
    
#### Step 2: CRDS Setup

The Roman pipeline relies on 'reference files' for processing data. Roman reference files are stored in the Calibration Reference Database System (CRDS). Access to it is enabled by the following environment variables:

	export CRDS_PATH=$HOME/crds_cache
	export CRDS_SERVER_URL=https://roman-crds-test.stsci.edu

Note that the above URL points to the TEST server which isn't publicly available but this is the way to set it up when a public server is online. The first time a reference file is accessed it is downloaded to the local cache. Subsequent uses of the file and offline access use the copy from the cache. Internally, at STScI the cache is available. For more information on CRDS consult the CRDS User Guide.

#### Step 3: Creating a conda environment

Create a new conda environment, called "roman-test". 

** Caution: The new environment will inherit the current one. That means that if you are in the base conda environment and there are packages in it they will be available in the new environment unless you reinstall them there. This is generally bad because Python will also load packages from that base environment. A case, which is often a source for confusion, is when ipython is not installed in the new environment but is available in the base one. Starting ipython works and loading a package may work but this package is imported from the base env and most often is a version different from what's desired.)

	% conda create -n roman-test python=3.9

Activate the environment and install ipython and numpy

	% conda activate roman-test
	% pip install jupyter
	% pip install numpy

#### Step 4: Installing the romancal pipeline

To install the latest public release of the pipeline:

	% pip install romancal

The correct versions of the dependencies will be pulled in. For detailed installation instructions including how to install the development version of the pipeline, or a specific version number, please see https://github.com/spacetelescope/romancal.

## Contributing to the Notebooks Repository

If you wish to make changes or add content to the notebooks in this repository, please:
	1. Fork this repository to your own account. The 'fork' button is in the upper right-hand corner.
	2. Clone your forked version to your machine.
	3. Make a branch with a name descriptive of the changes you'll be making.
	4. Commit these changes and push them to your remote fork.
	5. Open a pull request on the main notebooks repository. 

