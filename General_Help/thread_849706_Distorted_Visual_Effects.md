---
title: "Distorted Visual Effects"
date: 2008-07-04
forum: General Help
---

### Post by Aaron_Griffiths_92 on 2008-07-04
I recently downloaded a repack of ubuntu made by someone else on a torrent site and started using it... but i have found with my screenlets that I get a lot of distortion with animated effects... I tried installing my GFX card... a Nvidia 8600 GT, Which i have on an intel core 2duo e6750.
This is what console said.

aaron@aaron-desktop:~$ sudo apt-get nvidia-glx
[sudo] password for aaron: 
E: Invalid operation nvidia-glx
aaron@aaron-desktop:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni libgtk-jni libcairo-java libglib-jni
  libbcprov-java libglib-java libgtk-java
Use 'apt-get autoremove' to remove them.
Suggested packages:
  nvidia-kernel-source nvidia-settings
The following NEW packages will be installed
  nvidia-glx
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3853kB of archives.
After this operation, 12.3MB of additional disk space will be used.
Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-updates/restricted nvidia-glx 1:96.43.05+2.6.24.13-19.44 [3853kB]
Fetched 3853kB in 9s (402kB/s)                                                 
Selecting previously deselected package nvidia-glx.
(Reading database ... 217778 files and directories currently installed.)
Unpacking nvidia-glx (from .../nvidia-glx_1%3a96.43.05+2.6.24.13-19.44_i386.deb) ...
Setting up nvidia-glx (1:96.43.05+2.6.24.13-19.44) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
aaron@aaron-desktop:~$

---

### Post by Aaron_Griffiths_92 on 2008-07-05
anyone?

---

### Post by ajmorris on 2008-07-05
dont know if it will make much of a difference, but have you tried the nvidia-glx-new drivers as opposed to the nvidia-glx drivers?

---

### Post by sayakb on 2008-07-05
I had the same problem earlier with an Intel card (if that makes a difference). Afaik, this problem happens with compiz if you have too much graphics intensive programs running and get short of GPU memory.

---

