---
title: "Packages try to remove fglrx"
date: 2015-02-18
forum: General Help
---

### Post by paign10.ln on 2015-02-18
Recently, I formatted my computer (running Xubuntu 14.04). Everything installed just fine, except from 2 packages. Those 2 packages are libboost-all-dev and paraview. When I'm running apt-get, they try to remove fglrx.
```
paign10@paign10-labpc:~/Downloads$ sudo apt-get install paraview
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following extra packages will be installed:
  libcr0 libgl2ps0 libhdf5-7 libhwloc-plugins libhwloc5 libibverbs1
  libjsoncpp0 libnetcdfc++4 libnetcdfc7 libopenmpi1.6 libpq5 libqt4-help
  libtorque2 libvtk5.8 mpi-default-bin ocl-icd-libopencl1 openmpi-bin
  openmpi-common paraview-doc paraview-python python-vtk tcl-vtk
Suggested packages:
  blcr-dkms libhwloc-contrib-plugins libvtk5-dev vtk-examples vtk-doc
  opencl-icd gfortran openmpi-checkpoint hdf5-tools h5utils mayavi2
The following packages will be REMOVED:
  fglrx fglrx-amdcccle fglrx-core fglrx-dev
The following NEW packages will be installed:
  libcr0 libgl2ps0 libhdf5-7 libhwloc-plugins libhwloc5 libibverbs1
  libjsoncpp0 libnetcdfc++4 libnetcdfc7 libopenmpi1.6 libpq5 libqt4-help
  libtorque2 libvtk5.8 mpi-default-bin ocl-icd-libopencl1 openmpi-bin
  openmpi-common paraview paraview-doc paraview-python python-vtk tcl-vtk
0 upgraded, 23 newly installed, 4 to remove and 5 not upgraded.
Need to get 59,4 MB of archives.
After this operation, 125 MB disk space will be freed.
Do you want to continue? [Y/n] ^C
```

The Catalyst driver is the latest [Omega 14.12]("http://support.amd.com/en-us/download/desktop?os=Linux%20x86_64") driver from AMD. I built and installed the deb packages.
Any ideas on what's going on and how to deal with it?

---

### Post by paign10.ln on 2015-02-18
I removed fglrx. I installed the other packages, and then tried to reinstall fglrx. The problem showed up. Apparently there is a conflict with libopencl1.
There is a workaround, [here]("https://bugs.launchpad.net/ubuntu/+source/wine1.6/+bug/1376587").

---

