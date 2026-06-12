---
title: "Installing python-vtk on ubuntu 7.10"
date: 2008-01-21
forum: General Help
---

### Post by davemarsh on 2008-01-21
Hello,

I'm relatively new to the world of VTK but I will be using it in an upcoming class and I wanted to get all of the libraries installed. I found a bunch of topics relating to python-vtk but not this specific problem. When I do "sudo apt-get install python-vtk" I get the following result:

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
libwxgtk2.6-0 libjack0.100.0-0 libwxbase2.6-0 libfluidsynth1 ladcca2 scummvm
Use 'apt-get autoremove' to remove them.
Suggested packages:
vtk-examples vtk-doc mayavi
The following NEW packages will be installed:
python-vtk
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/3066kB of archives.
After unpacking 13.0MB of additional disk space will be used.
Selecting previously deselected package python-vtk.
(Reading database ... 124852 files and directories currently installed.)
Unpacking python-vtk (from .../python-vtk_5.0.3-1ubuntu1_i386.deb) ...
Setting up python-vtk (5.0.3-1ubuntu1) ...
Can't list /usr/lib/python2.5/site-packages/vtk
Can't list /usr/lib/python2.5/site-packages/vtk

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

Nothing seems to get installed and I can't find where it put the files. If I look in the synaptic package manager it thinks they're installed but that directory is not there.

Does anybody know what I am doing wrong?

Thank you

---

