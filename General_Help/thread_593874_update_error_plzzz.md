---
title: "update error plzzz"
date: 2007-10-27
forum: General Help
---

### Post by jayaramk on 2007-10-27
i installed avant window navigator applets and i got the folowing error none of the add\remove programs and update software is working and it says me to run sudo apt-get install -f

when i run it i get the error in the terminal....

jayaram@jayaram:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libcurl3
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libawn-bzr python-libawn-bzr
The following NEW packages will be installed:
  libawn-bzr python-libawn-bzr
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/87.8kB of archives.
After unpacking 279kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 103091 files and directories currently installed.)
Unpacking libawn-bzr (from .../libawn-bzr_0.2.0-bzr129-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libawn-bzr_0.2.0-bzr129-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libawn.so.0.0.1', which is also in package avant-window-navigator
Unpacking python-libawn-bzr (from .../python-libawn-bzr_0.2.0-bzr129-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr129-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/python2.5/site-packages/awn/awn.so', which is also in package avant-window-navigator
Errors were encountered while processing:
 /var/cache/apt/archives/libawn-bzr_0.2.0-bzr129-1_i386.deb
 /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr129-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
jayaram@jayaram:~$ 
jayaram@jayaram:~$ 



need a solution for this!!!!

---

### Post by disturbedite on 2007-10-27
this is no biggy, usually, i get this from time-to-time.
do this from command line:

sudo dpkg --force-overwrite -i /var/cache/apt/archives/libawn-bzr_0.2.0-bzr129-1_i386.deb  /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr129-1_i386.deb

or do them individually if that doesn't work for some reason:

sudo dpkg --force-overwrite -i /var/cache/apt/archives/libawn-bzr_0.2.0-bzr129-1_i386.deb
sudo dpkg --force-overwrite -i /var/cache/apt/archives/python-libawn-bzr_0.2.0-bzr129-1_i386.deb

---

### Post by jayaramk on 2007-10-27
thx it worked.....

---

### Post by disturbedite on 2007-10-27
no prob.

---

