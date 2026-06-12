---
title: "cuda installation error"
date: 2013-12-16
forum: General Help
---

### Post by shikshasmurthy on 2013-12-16
while i was trying to install some packages i got the following error:


dpkg: error processing /var/cache/apt/archives/cuda-visual-tools-5-5_5.5-22_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./usr/local/cuda-5.5/libnsight/plugins/org.eclipse.platform.doc.user_3.8.2.v20130121-201129.jar': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/cuda-extra-libs-5-5_5.5-22_i386.deb
 /var/cache/apt/archives/cuda-visual-tools-5-5_5.5-22_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


 i am working on ubuntu 12.04 LTS booted from 4 GB USB . there is still 1.9 GB free space left.but still i am getting an error of disk full error..
what should i do?.

---

### Post by steeldriver on 2013-12-17
Hello and welcome to the forums

"No space left on device" usually means exactly what it says - you need to free up some disk space (most likely on your root partition, but it may depend exactly what your partition scheme is) and then try again

---

### Post by NoBugs! on 2014-01-15
That's not much free space, 1.9gb.

Also, beware the black screen bug: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1268211](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1268211)
You may have to go back in the terminal and run the steps to re-set the nvidia graphics, after uninstalling CUDA.

---

