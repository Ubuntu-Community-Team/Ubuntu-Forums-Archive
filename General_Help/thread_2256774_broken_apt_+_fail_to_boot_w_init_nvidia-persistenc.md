---
title: "broken apt + fail to boot w/ init: nvidia-persistenced"
date: 2014-12-14
forum: General Help
---

### Post by Drone4four on 2014-12-14
X won’t start.  I can’t even get to gdm on boot.   When I boot, it’s just a black screen.  I used VTs to get my dmesg and to tinker with apt. My problem  might have something to do with a recent proprietary nvidia driver update.  

Here is my dmesg:
[https://www.dropbox.com/s/8coqimlgqgamxtc/dmesg14Dec2k14.txt?dl=0](https://www.dropbox.com/s/8coqimlgqgamxtc/dmesg14Dec2k14.txt?dl=0)
Take note near the end where it says:
```
 [17.227500] init: nvidia-persistenced main process (1999) terminated with status 1
```
I Googled that line and came across some forum threads related to corrupted nvidia drivers. As per some of the advice for other forum participants, I tried purging my system of everything nvidia with sudo apt-get purge nvidia-*, however I got this:
```
Reading package lists...
Building dependency tree...
Reading state information...
Package 'libgl1-nvidia-alternatives' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-glx' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-kernel-amd64' is not installed, so not removed
Package 'nvidia-kernel-686-pae' is not installed, so not removed
Package 'nvidia-kernel-486' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'libgl1-nvidia-glx' is not installed, so not removed
Package 'nvidia-cuda-debugger' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-compute-profiler' is not installed, so not removed
Package 'nvidia-cuda-profiler' is not installed, so not removed
Package 'nvidia-opencl-profiler' is not installed, so not removed
Package 'nvidia-settings-304' is not installed, so not removed
Package 'nvidia-settings-304-updates' is not installed, so not removed
Package 'nvidia-settings-310' is not installed, so not removed
Package 'nvidia-settings-310-updates' is not installed, so not removed
Package 'nvidia-settings-313-updates' is not installed, so not removed
Package 'nvidia-settings-319' is not installed, so not removed
Package 'nvidia-settings-319-updates' is not installed, so not removed
Package 'nvidia-settings-experimental-304' is not installed, so not removed
Package 'nvidia-settings-updates' is not installed, so not removed
Package 'nvidia-173' is not installed, so not removed
Package 'nvidia-173-dev' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-dev' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-310-updates-dev' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-313-updates-dev' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-experimental-310-dev' is not installed, so not removed
Package 'bumblebee-nvidia' is not installed, so not removed
Package 'boinc-nvidia-cuda' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-dev' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-304-updates-dev' is not installed, so not removed
Package 'nvidia-319-dev' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-319-updates-dev' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-dev' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-current-updates-dev' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-experimental-304-dev' is not installed, so not removed
Package 'nvidia-libopencl1-304' is not installed, so not removed
Package 'nvidia-libopencl1-304-updates' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-304' is not installed, so not removed
Package 'nvidia-opencl-icd-304-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'mate-sensors-applet-nvidia' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libelementary-bin : Depends: libefl but it is not going to be installed
 libelementary1 : Depends: libefl but it is not going to be installed
 terminology : Depends: elementary but it is not going to be installed

```
So apparently there aren’t very many nvidia proprietary drivers installed. I then tried installing an nvidia driver.  I picked 319 so as to avoid the buggy bleeding edge (like 33x version).  Here is me trying to install 319:
```

Reading package lists...
Building dependency tree...
Reading state information...
nvidia-319 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libelementary-bin : Depends: libefl but it is not going to be installed
 libelementary1 : Depends: libefl but it is not going to be installed
 nvidia-319-dev : Depends: nvidia-331-dev but it is not going to be installed
 nvidia-319-updates : Depends: nvidia-331-updates but it is not going to be installed
 nvidia-319-updates-dev : Depends: nvidia-331-updates-dev but it is not going to be installed
 terminology : Depends: elementary but it is not going to be installed

```
So I do have nvidia-319 already installed? If that’s true, then why when I tried to purge, did it say that it isn’t installed.  Back up there it does say:```
Package 'nvidia-319-dev' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-319-updates-dev' is not installed, so not removed
```
What is going on? As you can see, there are some corrupted EFL packages in my system, but I don’t think that has anything to do with x not being able to start.  I entered sudo apt-get install -f anyways.  See here:
```

Reading package lists...
Building dependency tree...
Reading state information...
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  emotion-generic-players evas-generic-loaders libefl libefl-bin libefl-data
  libelementary-bin libelementary1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  elementary libefl libefl-bin libefl-data
The following NEW packages will be installed:
  elementary libefl libefl-bin libefl-data
0 upgraded, 4 newly installed, 0 to remove and 4 not upgraded.
64 not fully installed or removed.
Need to get 0 B/15.1 MB of archives.
After this operation, 34.9 MB of additional disk space will be used.
(Reading database ... 658557 files and directories currently installed.)
Preparing to unpack .../libefl-data_1.11.3-0trusty0_all.deb ...
Unpacking libefl-data (1.11.3-0trusty0) ...
Preparing to unpack .../libefl-bin_1.11.3-0trusty0_amd64.deb ...
Unpacking libefl-bin (1.11.3-0trusty0) ...
Preparing to unpack .../libefl_1.11.3-0trusty0_amd64.deb ...
Unpacking libefl (1.11.3-0trusty0) ...
Preparing to unpack .../elementary_20140904-1_amd64.deb ...
Unpacking elementary (20140904-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...

```
To capture these shell messages, I used sudo apt-get -f install -y >>file.txt which for some reason broke half way through and didn’t finish capturing the rest of the output for my apt-get -f install.  Oh well.  

Anyways, is my broken package tool related to my experience with being unable to boot? What’s wrong with my system and what do I have to do to get x to start?  Is there any other information I can provide to help you ppl help me?

---

### Post by Drone4four on 2014-12-31
I have Ubuntu running perfectly now. The solution was simple.

I commented out my bodhi packages in my sources and then ran sudo apt-get autoremove -f . 

This automatically installed the latest kernel and then built an nvidia kernel module. This was previously getting blocked by the broken efl packages.

---

