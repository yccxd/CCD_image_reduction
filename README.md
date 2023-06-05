# CCD_image_reduction
A simple python script for astronomical image reduction  

# Structure of the file
LOT20xxXXXX /             #   
            / bias-dark   # containing bias and dark frames  
            / flat        # containing flat field and dedicated dark frames for the flat field (optional)  
!!! You can create a folder named 'BLKS' anywhere in the based folder.  
!!! Images in this folder will be ignored in this pipeline.  

# Setup environment variables
basepath = ''			            # relative or absolute path of the images
raw_path = basepath + 'RAW/'	# path includes RAW data
procpath = basepath + 'proc/'	# path for the calibrated output file

# Usage
  >> python3 imred.py <input_path> [-d] [-pdark] [-pflat] [-showls]
     input_path can be a folder (e.g. LOT20210123) or individual fits file(s) (*.fits/fit/fts)
     use -d for additional relative path of the input/output file
     -pdark and -pflat are optional arguments to assign the date of the dark/flat frames for the image reduction process
     -showls is an optional argument that only print the exposing parameters from fits header but do nothing about image reduction

# Output files and naming rules
All the calibrated fits file will be places in the given folder follow the structure:
LOT20xxXXXX /             # containing master dark/flat and the logfile 'proc.log'
            / targets     # containing all the calibrated scientific images
For the scientific images, filename with *_d.fit, *_f.fit, *_df.fit indicates image was dark subtracted, flat calibrated, and both calibrated, respectively. The master dark/flat will also appeared in the output folder, given the filename dark/flat_[binsize]_[expT/filter].fit

# Known issue and todo list
program abort when flatDlist do not fully covered the dark frame necessarily for the flat field reduction, try making another interpolation?
