---
title: "Errors in installing libyaml-cpp-dev"
date: 2015-05-18
forum: General Help
---

### Post by Shishir_Kolathaya on 2015-05-18
Hello,

I am using ubuntu 14.04 LTS. I was trying to install libyaml-cpp-dev in my computer and it did not work. Here is the list of sources:

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to


# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main


I ran this command:
sudo apt-get install libyaml-cpp-dev

Got the following error ( in the end )

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  collada-dom-dev collada-dom2.4-dp-base collada-dom2.4-dp-dev fltk1.3-doc
  fluid freeglut3 gazebo2 gir1.2-gtk-2.0 hddtemp liballegro4.4
  liballegro4.4-plugin-alsa libapr1 libapr1-dev libaprutil1 libaprutil1-dev
  libassimp-dev libassimp3 libatk1.0-dev libavcodec-dev libavformat-dev
  libavutil-dev libbz2-dev libcairo-script-interpreter2 libcairo2-dev
  libcegui-mk2-0.7.6 libcegui-mk2-dev libcf0 libconsole-bridge-dev
  libconsole-bridge0.2 libcurl4-openssl-dev libcv-dev libcvaux-dev
  libdc1394-22-dev libdevil-dev libdevil1c2 libflann-dev libflann1.8
  libfltk-cairo1.3 libfltk-forms1.3 libfltk-gl1.3 libfltk-images1.3 libfltk1.1
  libfltk1.3 libfltk1.3-dev libfontconfig1-dev libfreeimage-dev libfreeimage3
  libfreetype6-dev libgdk-pixbuf2.0-dev libgeos-3.4.2 libgeos-c1 libgl2ps-dev
  libgl2ps0 libglib2.0-dev libgnomecanvas2-0 libgnomecanvas2-common
  libgtk2.0-dev libharfbuzz-dev libharfbuzz-gobject0 libhdf5-7 libhighgui-dev
  libice-dev libidn11-dev libilmbase-dev libjasper-dev liblcms1-dev
  liblcms2-dev libldap2-dev liblodo3.0 liblog4cxx10 liblog4cxx10-dev
  liblua5.1-0 liblua5.1-0-dev liblz4-1 liblz4-dev libmng-dev libnetcdf-dev
  libnetcdfc++4 libnetcdfc7 libnetcdff5 libodbc1 libogg-dev libogre-1.8-dev
  libogre-1.8.0 libois-1.3.0 libopencv-calib3d-dev libopencv-contrib-dev
  libopencv-core-dev libopencv-dev libopencv-features2d-dev
  libopencv-flann-dev libopencv-gpu-dev libopencv-gpu2.4 libopencv-highgui-dev
  libopencv-imgproc-dev libopencv-legacy-dev libopencv-ml-dev
  libopencv-objdetect-dev libopencv-ocl-dev libopencv-ocl2.4
  libopencv-photo-dev libopencv-photo2.4 libopencv-stitching-dev
  libopencv-stitching2.4 libopencv-superres-dev libopencv-superres2.4
  libopencv-ts-dev libopencv-ts2.4 libopencv-video-dev libopencv-videostab-dev
  libopencv-videostab2.4 libopencv2.4-java libopencv2.4-jni libopenexr-dev
  libopenni-dev libopenni-sensor-pointclouds0 libopenni0 libpango1.0-dev
  libpcl-1.7-all libpcl-1.7-all-dev libpcl-1.7-bin libpcl-1.7-doc
  libpcl-apps-1.7 libpcl-apps-1.7-dev libpcl-common-1.7 libpcl-common-1.7-dev
  libpcl-features-1.7 libpcl-features-1.7-dev libpcl-filters-1.7
  libpcl-filters-1.7-dev libpcl-geometry-1.7-dev libpcl-io-1.7
  libpcl-io-1.7-dev libpcl-kdtree-1.7 libpcl-kdtree-1.7-dev
  libpcl-keypoints-1.7 libpcl-keypoints-1.7-dev libpcl-octree-1.7
  libpcl-octree-1.7-dev libpcl-outofcore-1.7 libpcl-outofcore-1.7-dev
  libpcl-people-1.7 libpcl-people-1.7-dev libpcl-recognition-1.7
  libpcl-recognition-1.7-dev libpcl-registration-1.7
  libpcl-registration-1.7-dev libpcl-sample-consensus-1.7
  libpcl-sample-consensus-1.7-dev libpcl-search-1.7 libpcl-search-1.7-dev
  libpcl-segmentation-1.7 libpcl-segmentation-1.7-dev libpcl-surface-1.7
  libpcl-surface-1.7-dev libpcl-tracking-1.7 libpcl-tracking-1.7-dev
  libpcl-visualization-1.7 libpcl-visualization-1.7-dev libpcre3-dev
  libpcrecpp0 libpixman-1-dev libplayerc++3.0 libplayerc3.0 libplayercommon3.0
  libplayercore3.0 libplayerdrivers3.0 libplayerinterface3.0 libplayerjpeg3.0
  libplayertcp3.0 libplayerwkb3.0 libpmap3.0 libpoco-dev libpococrypto9
  libpocodata9 libpocofoundation9 libpocomysql9 libpoconet9 libpoconetssl9
  libpocoodbc9 libpocosqlite9 libpocoutil9 libpocoxml9 libpocozip9 libprotoc8
  libpyside-dev libpyside-py3-1.2 libpyside1.2 libqhull-dev libqhull6
  libqwt-dev libqwt5-qt4 libqwt6 libraw1394-dev libraw1394-tools
  libreadline-dev libreadline6-dev librtmp-dev libsctp-dev libsctp1
  libsdformat-dev libsdformat1 libshiboken-dev libshiboken-py3-1.2
  libshiboken1.2 libsilly libsm-dev libstatgrab9 libswscale-dev libtbb-dev
  libtheora-dev libtinfo-dev libtinyxml-dev liburdfdom-dev
  liburdfdom-headers-dev liburdfdom-model-state0.2 liburdfdom-model0.2
  liburdfdom-sensor0.2 liburdfdom-world0.2 libvtk-java libvtk5-dev
  libvtk5-qt4-dev libvtk5.8 libvtk5.8-qt4 libxaw7-dev libxcb-shm0-dev
  libxcomposite-dev libxcursor-dev libxft-dev libxi-dev libxinerama-dev
  libxmu-dev libxmu-headers libxpm-dev libxrandr-dev libxrender-dev libxss-dev
  libxt-dev libzzip-0-13 libzzip-dev lksctp-tools opencv-data openni-utils
  python-matplotlib python-matplotlib-data python-netifaces python-opencv
  python-opengl python-psutil python-pydot python-pyparsing python-pyside
  python-pyside.phonon python-pyside.qtcore python-pyside.qtdeclarative
  python-pyside.qtgui python-pyside.qthelp python-pyside.qtnetwork
  python-pyside.qtopengl python-pyside.qtscript python-pyside.qtsql
  python-pyside.qtsvg python-pyside.qttest python-pyside.qtuitools
  python-pyside.qtwebkit python-pyside.qtxml python-qt4-dev python-qt4-gl
  python-qwt5-qt4 python-sip-dev python-support python-tz python-vtk
  robot-player ros-indigo-actionlib ros-indigo-actionlib-msgs
  ros-indigo-actionlib-tutorials ros-indigo-angles ros-indigo-bond
  ros-indigo-bond-core ros-indigo-bondcpp ros-indigo-bondpy
  ros-indigo-camera-calibration ros-indigo-camera-calibration-parsers
  ros-indigo-camera-info-manager ros-indigo-catkin ros-indigo-class-loader
  ros-indigo-cmake-modules ros-indigo-collada-parser ros-indigo-collada-urdf
  ros-indigo-common-msgs ros-indigo-common-tutorials
  ros-indigo-compressed-depth-image-transport
  ros-indigo-compressed-image-transport ros-indigo-control-msgs
  ros-indigo-cpp-common ros-indigo-cv-bridge ros-indigo-depth-image-proc
  ros-indigo-diagnostic-aggregator ros-indigo-diagnostic-analysis
  ros-indigo-diagnostic-common-diagnostics ros-indigo-diagnostic-msgs
  ros-indigo-diagnostic-updater ros-indigo-diagnostics
  ros-indigo-dynamic-reconfigure ros-indigo-eigen-conversions
  ros-indigo-eigen-stl-containers ros-indigo-executive-smach
  ros-indigo-filters ros-indigo-gencpp ros-indigo-genlisp ros-indigo-genmsg
  ros-indigo-genpy ros-indigo-geometric-shapes ros-indigo-geometry
  ros-indigo-geometry-msgs ros-indigo-geometry-tutorials
  ros-indigo-image-geometry ros-indigo-image-transport
  ros-indigo-joint-state-publisher ros-indigo-kdl-conversions
  ros-indigo-kdl-parser ros-indigo-message-filters
  ros-indigo-message-generation ros-indigo-message-runtime ros-indigo-nav-msgs
  ros-indigo-nodelet ros-indigo-nodelet-tutorial-math ros-indigo-octomap
  ros-indigo-orocos-kdl ros-indigo-pluginlib ros-indigo-pluginlib-tutorials
  ros-indigo-python-orocos-kdl ros-indigo-random-numbers
  ros-indigo-resource-retriever ros-indigo-rosbag
  ros-indigo-rosbag-migration-rule ros-indigo-rosbag-storage
  ros-indigo-rosbuild ros-indigo-rosclean ros-indigo-rosconsole
  ros-indigo-rosconsole-bridge ros-indigo-roscpp
  ros-indigo-roscpp-serialization ros-indigo-roscpp-traits ros-indigo-rosgraph
  ros-indigo-rosgraph-msgs ros-indigo-roslaunch ros-indigo-roslib
  ros-indigo-roslz4 ros-indigo-rosmaster ros-indigo-rosmsg ros-indigo-rosnode
  ros-indigo-rosout ros-indigo-rospack ros-indigo-rosparam ros-indigo-rospy
  ros-indigo-rosservice ros-indigo-rostest ros-indigo-rostime
  ros-indigo-rostopic ros-indigo-rosunit ros-indigo-roswtf
  ros-indigo-self-test ros-indigo-sensor-msgs ros-indigo-shape-msgs
  ros-indigo-shape-tools ros-indigo-smach ros-indigo-smach-msgs
  ros-indigo-smach-ros ros-indigo-smclib ros-indigo-std-msgs
  ros-indigo-std-srvs ros-indigo-stereo-msgs ros-indigo-tf
  ros-indigo-tf-conversions ros-indigo-tf2 ros-indigo-tf2-msgs
  ros-indigo-tf2-py ros-indigo-tf2-ros ros-indigo-topic-tools
  ros-indigo-trajectory-msgs ros-indigo-turtle-actionlib ros-indigo-turtle-tf
  ros-indigo-turtle-tf2 ros-indigo-turtlesim ros-indigo-urdf
  ros-indigo-urdf-parser-plugin ros-indigo-visualization-msgs
  ros-indigo-xmlrpcpp sbcl shiboken sip-dev tango-icon-theme tcl-vtk
  tcl8.6-dev tk8.6-dev uuid-dev x11proto-composite-dev x11proto-randr-dev
  x11proto-render-dev x11proto-scrnsaver-dev x11proto-xinerama-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libyaml-cpp-dev
0 upgraded, 1 newly installed, 0 to remove and 424 not upgraded.
456 not fully installed or removed.
Need to get 0 B/339 kB of archives.
After this operation, 1,460 kB of additional disk space will be used.
(Reading database ... 305597 files and directories currently installed.)
Preparing to unpack .../libyaml-cpp-dev_0.5.1-1_amd64.deb ...
Unpacking libyaml-cpp-dev (0.5.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/libyaml-cpp-dev_0.5.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/pkgconfig/yaml-cpp.pc', which is also in package yaml-cpp 0.2.7-5precise-20120502-0513-+0000
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libyaml-cpp-dev_0.5.1-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Note: I was trying to install ros-indigo which lead to this dependency problem. Any help is appreciated. Thanks.

---

