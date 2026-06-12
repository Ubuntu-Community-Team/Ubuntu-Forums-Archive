---
title: "Cannot download updates/software"
date: 2007-04-29
forum: General Help
---

### Post by arkiedan on 2007-04-29
This is a new install of Ubuntu 7.04. Trying to update software and get the following:

Updater:

"Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

Tried Synaptic and got:

"An error occured

E: libgtkmm-2.4-1c2a: subprocess post-removal script returned error exit status 132
E: libcairomm-1.0-1: subprocess post-removal script returned error exit status 132
E: libdebconfclient0: subprocess post-removal script returned error exit status 132
E: libdebian-installer4: subprocess post-removal script returned error exit status 132
E: libdiscover1: subprocess post-removal script returned error exit status 132
E: libfuse2: subprocess post-removal script returned error exit status 132
E: libglibmm-2.4-1c2a: subprocess post-removal script returned error exit status 132
E: libntfs9: subprocess post-removal script returned error exit status 132
E: xfsprogs: subprocess post-removal script returned error exit status 132"

Tried Apt-get and got:

"dan@dan-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libcairomm-1.0-1 libdebconfclient0 libdebian-installer4 libdiscover1
  libfuse2 libglibmm-2.4-1c2a libgtkmm-2.4-1c2a libntfs9 xfsprogs
0 upgraded, 0 newly installed, 9 to remove and 11 not upgraded.
9 not fully installed or removed.
Need to get 0B of archives.
After unpacking 9171kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 88001 files and directories currently installed.)
Removing libgtkmm-2.4-1c2a ...
Illegal instruction (core dumped)
dpkg: error processing libgtkmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 132
Removing libcairomm-1.0-1 ...
Illegal instruction (core dumped)
dpkg: error processing libcairomm-1.0-1 (--remove):
 subprocess post-removal script returned error exit status 132
Removing libdebconfclient0 ...
Illegal instruction (core dumped)
dpkg: error processing libdebconfclient0 (--remove):
 subprocess post-removal script returned error exit status 132
Removing libdebian-installer4 ...
Illegal instruction (core dumped)
dpkg: error processing libdebian-installer4 (--remove):
 subprocess post-removal script returned error exit status 132
Removing libdiscover1 ...
Illegal instruction (core dumped)
dpkg: error processing libdiscover1 (--remove):
 subprocess post-removal script returned error exit status 132
Removing libfuse2 ...
Illegal instruction (core dumped)
dpkg: error processing libfuse2 (--remove):
 subprocess post-removal script returned error exit status 132
Removing libglibmm-2.4-1c2a ...
Illegal instruction (core dumped)
dpkg: error processing libglibmm-2.4-1c2a (--remove):
 subprocess post-removal script returned error exit status 132
Removing libntfs9 ...
Illegal instruction (core dumped)
dpkg: error processing libntfs9 (--remove):
 subprocess post-removal script returned error exit status 132
Removing xfsprogs ...
Illegal instruction (core dumped)
dpkg: error processing xfsprogs (--remove):
 subprocess post-removal script returned error exit status 132
Errors were encountered while processing:
 libgtkmm-2.4-1c2a
 libcairomm-1.0-1
 libdebconfclient0
 libdebian-installer4
 libdiscover1
 libfuse2
 libglibmm-2.4-1c2a
 libntfs9
 xfsprogs
E: Sub-process /usr/bin/dpkg returned an error code (1)
dan@dan-desktop:~$ "

Anyone have any ideas? Anyone?  

Running with Windows XP on hda, photographs on hdb and PCLinuxOS and Ubuntu on hd3 c

Dan

---

### Post by Ekeluo on 2007-04-29
Reload you index using sudo apt-get update.
If this doesn't work and you have the live CD, boot to it and copy /var/apt/cache/archives directory and paste it to your hard drive(you'll probably need an external hard drive of some sort to do this.) Overwrite all files (do this only if you're sure you haven't downloaded any software before.)

---

### Post by arkiedan on 2007-04-29
Thanks for the help

I'll see if I can figure that out after church. I don't have an external drive and so that will probably be a problem. If nothing else I'll reinstall.

---

### Post by schurem on 2007-08-16
I have the exact same problem as the original poster. Exact same packages too. However, i do have managed to get the internet connection working, and ran apt-get update. apt-get install -f still returns the same errors. It seems something goes horribly wrong in the removal of said nine packages. Maybe it has something to do with the fact that this is a brand spanking new box, core2duo, the works? "illegal instruction core dumped", that cant be right...

Anyway, i did the dumb windows thing and reinstalled from the cd, after having it run an integrity check on itself. now the error seems to have gone away. Whiskey Tango Foxtrot.

---

### Post by honeydew on 2007-08-22
grrrar!!! Im having the same issues..

---

