# Real Time AI-based-vehicle-detection
The objective of the program given is to detect object of interest(Car) in video frames and to keep tracking the same object. This is an example of how to detect vehicles in Python.
Real-time vehicle detection is one of the many application of object detection, whereby focuses on detecting cars within an image together with the location coordinates.
The startling losses both in human lives and finance caused by vehicle accidents.
Detecting vehicles in images acquired from a moving platform is a challenging problem.
vehicle detection together with road detection is heavily applied on ** self-driving cars*, for a car to navigate safely along the road, it has to know where other cars are positioned so as it can avoid a collision.
## how to operate:
### step 1: Place the car image in front of camera
### step 2: Vehicle car detection is displaying on the LCD screen 
### step 3: Vehicle Detection marked with Red rectange Region with CAR name 

# Circuit Diagram 
![AI Vehicle Detection System CAM](https://user-images.githubusercontent.com/42414598/137729468-31b161e6-92cc-4f7e-8bde-9600d00e6e76.jpg)


## Resources
Material Required for the Projects 
## Hardwares 
* Raspberry Pi 4
* USB web Camera
* 7 inch LCD display screen 
* Power sources 
## Programming 
* OpenCV Package 4.5
* Python 3.9 
* Pre-trained Cascade classifier
# Methodology
Hardware connections very important which provides the overview of circuit in the project , if connections are correct then output will be displayed on the screen of LCD   
Python is a wonderful and powerful programming language that's easy to use (easy to read and write) and, with Raspberry Pi, lets you connect your project to the real world.
## Step 1: Install Python Packages 
* A package is basically a directory with Python files and a file with the name __init__.py. This means that every directory inside of the Python path, which contains a file named __init__.py, will be treated as a package by Python. It's possible to put several modules into a Package.
* Raspberry pi operated by Raspbian is a Debian-based engineered especially for the Raspberry Pi and it is the perfect general-purpose OS for Raspberry users 
* Install Raspberry pi GPIO packages: pip install RPi.GPIO
* Type " pinout " in Terminal of Raspberry pi 
## Step 2 : Install Opencv in Raspberry pi  
###### to get the current status
* $ sudo rpi-eeprom-update
###### if needed, to update the firmware
* $ sudo rpi-eeprom-update -a
* $ sudo reboot 
###### Version check.
Before you install OpenCV on your Raspberry Pi 4, it is time for a final version check. Many readers just jump into the guide, skipping the introduction, often because they have already an operating system working. For those, please give the command uname -a and check your version.
* $ python3 --version
###### Dependencies.
The OpenCV software uses other third-party software libraries. These have to be installed first. Some come with the Raspbian operating system, others may have been gathered over time, but it's better to be safe than sorry, so here is the complete list. Only the latest packages are installed by the procedure.
* $ sudo apt-get update
* $ sudo apt-get upgrade
* $ sudo apt-get install cmake gfortran
* $ sudo apt-get install libjpeg-dev libtiff-dev libgif-dev
* $ sudo apt-get install libavcodec-dev libavformat-dev libswscale-dev
* $ sudo apt-get install libgtk2.0-dev libcanberra-gtk*
* $ sudo apt-get install libxvidcore-dev libx264-dev libgtk-3-dev
* $ sudo apt-get install libtbb2 libtbb-dev libdc1394-22-dev libv4l-dev
* $ sudo apt-get install libopenblas-dev libatlas-base-dev libblas-dev
* $ sudo apt-get install libjasper-dev liblapack-dev libhdf5-dev
* $ sudo apt-get install protobuf-compiler
* $ sudo apt-get install qt5-default
* $ cd ~
* $ wget -O opencv.zip https://github.com/opencv/opencv/archive/4.5.0.zip
* $ wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/4.5.0.zip

* $ unzip opencv.zip
* $ unzip opencv_contrib.zip
* $ mv opencv-4.5.0 opencv
* $ mv opencv_contrib-4.5.0 opencv_contrib
###### Install a virtual environment.
Step one is some administration. We only use Python 3 because the support of Python 2.7 has stopped at the beginning of 2020. You have first to determine your Python 3 version   and location.
The Python location in the above commands was /usr/bin/python3.7. This location is passed as an argument in the echo command. The next step is installing the virtual      environment software. This can be done with the following commands.
* $ sudo pip3 install virtualenv
* $ sudo pip3 install virtualenvwrapper
* $ echo "export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python3.7" >> ~/.bashrc
###### reload profile
* $ source ~/.bashrc
* $ echo "export WORKON_HOME=$HOME/.virtualenvs" >> ~/.bashrc
* $ echo "source /usr/local/bin/virtualenvwrapper.sh" >> ~/.bashrc
* $ source ~/.bashrc
* $ mkvirtualenv cv450
###### without sudo!!!!
* $ pip3 install numpy
##### Build Make 
* $ cd ~/opencv/
* $ mkdir build
* $ cd build
* $ cmake -D CMAKE_BUILD_TYPE=RELEASE \
          -D CMAKE_INSTALL_PREFIX=/usr/local \
          -D OPENCV_EXTRA_MODULES_PATH=~/opencv_contrib/modules \
          -D ENABLE_NEON=ON \
          -D ENABLE_VFPV3=ON \
          -D WITH_OPENMP=ON \
          -D WITH_OPENCL=OFF \
          -D BUILD_TIFF=ON \
          -D WITH_FFMPEG=ON \
          -D WITH_TBB=ON \
          -D BUILD_TBB=ON \
          -D BUILD_TESTS=OFF \
          -D WITH_EIGEN=OFF \
          -D WITH_GSTREAMER=OFF \
          -D WITH_V4L=ON \
          -D WITH_LIBV4L=ON \
          -D WITH_VTK=OFF \
          -D WITH_QT=OFF \
          -D OPENCV_ENABLE_NONFREE=ON \
          -D INSTALL_C_EXAMPLES=OFF \
          -D INSTALL_PYTHON_EXAMPLES=OFF \
          -D BUILD_opencv_python3=TRUE \
          -D OPENCV_GENERATE_PKGCONFIG=ON \
          -D BUILD_EXAMPLES=OFF ..
 * Before we can start the actual build, the memory swap space needs to be enlarged. For daily use a swap memory of 100 Mbyte is sufficient. However, with the massive build ahead of use, extra memory space is crucial. Enlarge the swap space with the following command.
* $ sudo nano /etc/dphys-swapfile
* This command opens Nano, a very lightweight text editor, with the system file dphys-swapfile. With the arrow keys, you can move the cursor to the CONF_SWAPSIZE line where the new value 2048 can be entered. Next, close the session with the <Ctrl+X> key combination. With <Y> and <Enter> changes are being saved in the same file.
* $ sudo /etc/init.d/dphys-swapfile stop
* $ sudo /etc/init.d/dphys-swapfile start
* $ make -j4
###### Make.
Now everything is ready for the great build. This takes a lot of time. Be very patient is the only advice here. Don't be surprised if at 99% your build seems to be crashed. That is 'normal' behaviour. Even when your CPU Usage Monitor gives very low ratings like 7%. In reality, your CPU is working so hard it has not enough time to update these usage numbers correctly.
You can speed things up with four cores working simultaneously (make -j4). On a Raspberry Pi 4, it takes just over an hour to build the whole library. Sometimes the system crashes for no apparent reason at all at 99% or even 100%. In that case, restart all over again, as explained at the end of this page, and rebuild with make -j1.
Probably you get a whole bunch of warnings during the make. Don't pay to much attention to it. They are generated by subtle differences in template overload functions due to little version differences. 
* $ sudo make install
* $ sudo ldconfig
###### cleaning (frees 300 KB)
* $ make clean
* $ sudo apt-get update
## Step 3: Steps to implement AI Based car detection with Python & OpenCV:
Imports:
#### import cv2
#### import os
Initialize the classifier:
#### cascPath=os.path.dirname(cv2.file)+"/data/car.xml"
#### faceCascade = cv2.CascadeClassifier(cascPath)
Apply faceCascade on webcam frames:
code : https://github.com/AICRA-Projects/AI-based-vehicle-detection/blob/main/cars.xml

## Cascade Classifier: 
Object Detection using Haar feature-based cascade classifiers is an effective object detection method proposed by Paul Viola and Michael Jones in their paper, "Rapid Object Detection using a Boosted Cascade of Simple Features" in 2001. It is a machine learning based approach where a cascade function is trained from a lot of positive and negative images. It is then used to detect objects in other images.
Here we will work with car detection. Initially, the algorithm needs a lot of positive images (images of faces) and negative images (images without faces) to train the classifier. Then we need to extract features from it. For this, Haar features shown in the below image are used. They are just like our convolutional kernel. Each feature is a single value obtained by subtracting sum of pixels under the white rectangle from sum of pixels under the black rectangle.
* The car.xml can be downloaded here: https://github.com/AICRA-Projects/AI-based-vehicle-detection

## Step 5 : Auto run script in Raspberry pi
Method 1: rc.local You will need root-level access to modify rc.local, so do so with sudo:

sudo nano /etc/rc.local
Scroll down, and just before the exit 0 line, enter the following:

python /home/pi/blink.py &
## Step 6: Give Power to the robot by connecting White Usb Cable with USB connector of Power Bank
          
# Conclusion 
Vehicle detection reliability offers advantages for site safety and traffic control. Identifying the perfect technology for your requirements can be challenging for a vehicle detection application. Some of the factors that can play a major role in the success of a vehicle detection system are application environment (indoors or outdoors) , sensor mounting, sensing range, and target size.
# Reference 
* https://www.engineeringbigdata.com/vehicle-detection-opencv-python-cv2/
* https://projects.raspberrypi.org/en/projects/using-pip-on-raspberry-pi
* https://www.raspberrypi.org/documentation/usage/python/
* https://qengineering.eu/install-opencv-4.5-on-raspberry-pi-4.html
