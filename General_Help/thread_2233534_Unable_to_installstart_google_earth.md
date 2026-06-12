---
title: "Unable to install/start google earth"
date: 2014-07-09
forum: General Help
---

### Post by sofasurfer on 2014-07-09
I have read and used a few differant threads to install google on Ubuntu 14.04. So far I am a failure. 
I tried to verify my cpu... 
$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2

I think I have a 32 bit cpu. Why does it say "CPU op-mode(s): 32-bit, 64-bit"?

My Ubuntu version is 32 bit I think... 
$ uname -a
Linux daryl-H61M-S2PV 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:43:42 UTC 2014 i686 i686 i686 GNU/Linux

How to install Google earth? Never had this much trouble with it before.

---

### Post by slickymaster on 2014-07-09
> **sofasurfer said:**
> I have read and used a few differant threads to install google on Ubuntu 14.04. So far I am a failure. 
I tried to verify my cpu... 
$ lscpu
Architecture:          i686
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2

I think I have a 32 bit cpu. Why does it say "CPU op-mode(s): 32-bit, 64-bit"?
Your architecture is i686 and your CPU supports both 32-bit and 64-bit operating modes. 
> **sofasurfer said:**
> My Ubuntu version is 32 bit I think... 
$ uname -a
Linux daryl-H61M-S2PV 3.13.0-30-generic #55-Ubuntu SMP Fri Jul 4 21:43:42 UTC 2014 i686 i686 i686 GNU/Linux

You're running a 32-bit kernel, which means that you can only run 32-bit apps. You won't be able to install x64 built applications since they're built specifically for x64 architectures.

> **sofasurfer said:**
> How to install Google earth? Never had this much trouble with it before.

For Ubuntu 32bit, simply [download Google Earth]("http://www.google.com/earth/download/ge/agree.html") and install it using Ubuntu Software Center, GDebi, dpkg or whatever you prefer.

---

### Post by sofasurfer on 2014-07-09
I extracted the file to my home folder. I do not see it even though it said "extraction completed. Now I am wondering how many copies I have installed. Hope I am not creating a mess.

---

### Post by slickymaster on 2014-07-09
> **sofasurfer said:**
> I extracted the file to my home folder. I do not see it even though it said "extraction completed. Now I am wondering how many copies I have installed. Hope I am not creating a mess.

Make sure the **lsb-core** package is installed! If not, open a terminal and run```
sudo apt-get install lsb-core
```After that just double-click the downloaded .deb package to install it using the Ubuntu Software Center.

You should find Google Earth in the Applications -> Internet menu or through the Dash.

---

### Post by sofasurfer on 2014-07-09
~$ sudo apt-get install lsb-core
[sudo] password for daryl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I downloaded the file, extracted it to home folder and it creates a folder called "Debian". This folder contains 4 files, "control", "postinst", "postrm" and "prerm". I have no clue what to do with them. I type obvious names (googleearth, google-earth, etc) into terminal but it does not start. I found nothing in the dash.

Hmmmmmm.........

---

### Post by slickymaster on 2014-07-09
See this: [https://help.ubuntu.com/community/GoogleEarth#Alternative_installation_method](https://help.ubuntu.com/community/GoogleEarth#Alternative_installation_method)

---

### Post by sofasurfer on 2014-07-09
I followed the instructions and this was the result when I installed the package.................

$ sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_i386.deb
Selecting previously unselected package googleearth.
(Reading database ... 213854 files and directories currently installed.)
Preparing to unpack googleearth_6.0.3.2197+1.1.0-1_i386.deb ...
Unpacking googleearth (6.0.3.2197+1.1.0-1) ...
dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on libfreeimage3; however:
  Package libfreeimage3 is not installed.

dpkg: error processing package googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Errors were encountered while processing:
 googleearth

---

### Post by sofasurfer on 2014-07-09
I followed the instructions and this was the result when I installed the package.................

$ sudo dpkg -i googleearth_6.0.3.2197+1.1.0-1_i386.deb
Selecting previously unselected package googleearth.
(Reading database ... 213854 files and directories currently installed.)
Preparing to unpack googleearth_6.0.3.2197+1.1.0-1_i386.deb ...
Unpacking googleearth (6.0.3.2197+1.1.0-1) ...
dpkg: dependency problems prevent configuration of googleearth:
 googleearth depends on libfreeimage3; however:
  Package libfreeimage3 is not installed.

dpkg: error processing package googleearth (--install):
 dependency problems - leaving unconfigured
Processing triggers for mime-support (3.54ubuntu1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Errors were encountered while processing:
 googleearth

---

### Post by slickymaster on 2014-07-09
Have you tried```
sudo apt-get install libfreeimage3
```

---

