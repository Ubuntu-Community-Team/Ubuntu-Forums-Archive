---
title: "Blender crashing after Xubuntu 14.04 upgrade"
date: 2014-04-21
forum: General Help
---

### Post by charlie_b on 2014-04-21
Not sure exactly where to put this problem so I'm putting it here in general help, although it arose as a consequence of an upgrade and specifically involves Blender.   I have been using Xubuntu 14.04 beta 2 for the last 8 weeks or so, and it has been working fine. With the official release of 14.04 last week I upgraded to the official release version.  Now I have a serious problem using Blender. I have been using Blender 2.69 in the Xubuntu 14.04 beta version and it has been working perfectly.   Since the upgrade it has started crashing. The particulars are: I do a lot of video editing work in Blender, and I make heavy use of the Camera Tracker and Object Tracker functions. As mentioned, these were working perfectly before the upgrade.  Since the upgrade, if I load a video, put a bunch of tracking markers on it, then try either the Camera Solve button or Object Solve button, Blender freezes and closes. This problem is consistent and repeatable.   The error messages in the apport log are as follows:    ERROR: apport (pid 3492) Mon Apr 21 17:08:18 2014: called for pid 3226, signal 6, core limit 0 ERROR: apport (pid 3492) Mon Apr 21 17:08:18 2014: executable: /usr/bin/blender (command line "blender") ERROR: apport (pid 3492) Mon Apr 21 17:08:18 2014: executable version is blacklisted, ignoring I haven't come across a problem like this before and I'm stumped to know what to do about it.

---

### Post by charlie_b on 2014-04-21
Another problem - I did not write the above in a solid block the way it appears. It was properly formatted with paragraphs and newlines. When I posted it, it appeared with paragraphs and newlines all deleted. I've tried editing it but that did no good.

---

### Post by gondrano2 on 2014-11-30
I people, I would like to run blender under xubuntu but it just freeze at starting panel. Can't focus on what the problem is. 
When I launch it via terminal, it shows the following:

[I]Color management: using fallback mode for management
connect failed: No such file or directory[/I]

Does my system require an icc profile not yet installed? or is a hardware problem? 

OS = Ubuntu 14.04 (trusty) 3.13.0-40-generic
CPU = 2 Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz, 1000.000 MHz, 2048 KB
Memory = 1000 MiB
Graphic card = Nvidia GeForceGO 7300 (not sure if installed)

thanks in advance

---

### Post by gondrano2 on 2014-11-30
Should b some problems with graphic card and Xserver:
I tryed to install some (following) Nvidia drivers but with poor results
NVIDIA-Linux-x86-340.58.run
NVIDIA-Linux-x86-304.123.run
NVIDIA-Linux-armv7l-gnueabihf-340.58.run
nvidia-installer log file '/var/log/nvidia-installer.log'
creation time: Sun Nov 30 15:47:16 2014
installer version: 304.123

PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

hereby is the log file output:

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1101' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

It seems not possible to install the drivers under xserver... but I have read of people able to use blender under xubuntu...

Any help?

---

