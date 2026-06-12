---
title: "How do I install Adobe Air?"
date: 2017-02-13
forum: General Help
---

### Post by jsc12345 on 2017-02-13
I'm encountering problems with installing Adobe Air on my Yakkety system. I already have the official .bin installer and an unofficial .deb package. When I open the .deb and click install, the process stops after a second or two. I can't work out how to get the .bin to work. Please help!
The Solution to this problem is, once you get the .bin installer, run these commands: ```
[FONT=Ubuntu Mono][COLOR=#000000] 
[/COLOR][/FONT]sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libbz2-1.0:i386 libgtk2.0-0:i386 libnss3:i386 libxaw7:i386 
```. Do anything the terminal tells you to.  Hope this helped!

---

### Post by wildmanne39 on 2017-02-13
*Thread moved to **General Help**.*

---

### Post by mastablasta on 2017-02-13
run the deb in terminal to see what the error output is.

---

### Post by howefield on 2017-02-13
> **jsc12345 said:**
> I already have the official .bin installer...

My understanding is that Adobe Air is no longer supported on Linux, can you link to where you got the "*official*" file..

---

### Post by jsc12345 on 2017-02-13
@howefeild, I got it from the Adobe AIR SDK archive at [https://helpx.adobe.com/air/kb/archived-air-sdk-version.html](https://helpx.adobe.com/air/kb/archived-air-sdk-version.html). @mastablasta, I'm not quite sure how to do that. Instructions?

---

### Post by howefield on 2017-02-13
> **jsc12345 said:**
> @howefeild, I got it from the Adobe AIR SDK archive at [https://helpx.adobe.com/air/kb/archived-air-sdk-version.html](https://helpx.adobe.com/air/kb/archived-air-sdk-version.html). 

That's what I thought, version 2.6 when the current version is 24 or thereabouts ? 

> @mastablasta, I'm not quite sure how to do that. Instructions?

If you are using Ubuntu 16.04 or later you could use apt..

```
sudo apt install -s ~/Downloads/name_of_package
```

Assuming the deb package is in your Downloads folder and the -s switch to simulate rather than attempt an actual install and use the actual names of the package.

---

### Post by jsc12345 on 2017-02-13
I have a new question. When I try edit the permissions of the .bin file, it says I can run it as a programmable executable. But when I double-click it I get an error message: This file is of an unknown type.

---

### Post by jsc12345 on 2017-02-14
Well, I've found the .deb's problem. It requires dependencies that Ubuntu can't find. Any ideas on installing from the .bin?

---

### Post by vasa1 on 2017-02-14
> **jsc12345 said:**
> Well, I've found the .deb's problem. It requires dependencies that Ubuntu can't find. ...
Posting the entire output will be more useful.

Edit: did you see [http://www.noobslab.com/2015/05/adobeair-is-now-available-for-ubuntu.html](http://www.noobslab.com/2015/05/adobeair-is-now-available-for-ubuntu.html) AdobeAir Is Now Available For Ubuntu 16.10/16.04/14.04/12.04/Linux Mint 18/17/13 [Updated]

That was the fourth link from the top when I Googled for **"adobe air" linux**.

---

### Post by jsc12345 on 2017-02-14
Fine. full out put is: ```
 Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Note, selecting 'adobeair' instead of '/home/sam/Downloads/adobeair_2.6.0.19170-devolo1_amd64.deb'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 adobeair : Depends: ia32-libs-gtk but it is not installable or
                     devolo-ia32-libs but it is not installable
E: Unable to correct problems, you have held broken packages 
```

---

### Post by Perfect Storm on 2017-02-14
```
sudo dpkg --add-architecture i386
sudo apt-get update
```

---

### Post by jsc12345 on 2017-02-14
I tried the solution at noobslab.com, but when I got to the second command, it did this: ```
 sudo dpkg -i adobe-air_amd64.deb[sudo] password for lori:               
Selecting previously unselected package adobeair.
(Reading database ... 296606 files and directories currently installed.)
Preparing to unpack adobe-air_amd64.deb ...
Unpacking adobeair (1:2.6.0.2) ...
dpkg: dependency problems prevent configuration of adobeair:
 adobeair depends on libbz2-1.0:i386.
 adobeair depends on libgtk2.0-0:i386 (>= 2.6).
 adobeair depends on libnss3:i386.
 adobeair depends on libxaw7:i386.


dpkg: error processing package adobeair (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 adobeair

```
Ideas?

---

### Post by Perfect Storm on 2017-02-14
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libbz2-1.0:i386 libgtk2.0-0:i386 libnss3:i386 libxaw7:i386
```

---

### Post by jsc12345 on 2017-02-15
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgtk2.0-0:i386 : Depends: libatk1.0-0:i386 (>= 1.32.0) but it is not going to be installed
                    Depends: libgdk-pixbuf2.0-0:i386 (>= 2.22.0) but it is not going to be installed
                    Depends: libpango-1.0-0:i386 (>= 1.28.3) but it is not going to be installed
                    Depends: libpangocairo-1.0-0:i386 (>= 1.28.3) but it is not going to be installed
                    Depends: libpangoft2-1.0-0:i386 (>= 1.28.3) but it is not going to be installed
                    Recommends: libgail-common:i386 but it is not going to be installed
 libnss3:i386 : Depends: libnspr4:i386 (>= 2:4.12) but it is not going to be installed
 libxaw7:i386 : Depends: libxmu6:i386 but it is not going to be installed
                Depends: libxt6:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
lori@ubuntu:~$ sudo apt-get -f install
[sudo] password for lori:               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  guile-2.0-libs libart-2.0-2 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libclass-data-inheritable-perl
  libclass-method-modifiers-perl libcommon-sense-perl
  libcrypt-openssl-bignum-perl libcrypt-openssl-rsa-perl libdata-random-perl
  libextutils-depends-perl libextutils-pkgconfig-perl libfile-which-perl
  libgc1c2 libgd-perl libglade2-0 libgnome-2-0 libgnome2-0 libgnome2-bin
  libgnome2-canvas-perl libgnome2-common libgnome2-gconf-perl libgnome2-perl
  libgnome2-vfs-perl libgnome2-wnck-perl libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-common libgnomevfs2-extra libgoo-canvas-perl
  libgoocanvas-common libgoocanvas3 libgtk2-appindicator-perl
  libgtk2-imageview-perl libgtk2-unique-perl libgtkimageview0
  libhttp-server-simple-perl libimage-magick-perl libimage-magick-q16-perl
  libjson-perl libjson-xs-perl libmagick++-6.q16-5v5 libmouse-perl
  libnet-dropbox-api-perl libnet-oauth-perl libnetpbm10 liborbit-2-0
  libpath-class-perl libproc-processtable-perl libproc-simple-perl
  libsort-naturally-perl libtypes-serialiser-perl libunique-1.0-0
  libwnck-common libwnck22 libwww-mechanize-perl libxml++2.6-2v5
  linux-headers-4.8.0-34 linux-headers-4.8.0-34-generic
  linux-image-4.8.0-34-generic linux-image-extra-4.8.0-34-generic
  linux-signed-image-4.8.0-34-generic netpbm perlmagick synfig-examples
  ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libatk1.0-0:i386 libbz2-1.0:i386 libdatrie1:i386 libgail-common:i386
  libgail18:i386 libgdk-pixbuf2.0-0:i386 libgraphite2-3:i386 libgtk2.0-0:i386
  libharfbuzz0b:i386 libice6:i386 libnspr4:i386 libnss3:i386
  libpango-1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386
  libsm6:i386 libthai0:i386 libxaw7:i386 libxmu6:i386 libxt6:i386
Suggested packages:
  librsvg2-common:i386 gvfs:i386
The following NEW packages will be installed:
  libatk1.0-0:i386 libbz2-1.0:i386 libdatrie1:i386 libgail-common:i386
  libgail18:i386 libgdk-pixbuf2.0-0:i386 libgraphite2-3:i386 libgtk2.0-0:i386
  libharfbuzz0b:i386 libice6:i386 libnspr4:i386 libnss3:i386
  libpango-1.0-0:i386 libpangocairo-1.0-0:i386 libpangoft2-1.0-0:i386
  libsm6:i386 libthai0:i386 libxaw7:i386 libxmu6:i386 libxt6:i386
0 upgraded, 20 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
Need to get 4,596 kB of archives.
After this operation, 15.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libbz2-1.0 i386 1.0.6-8build1 [30.9 kB]
Get:2 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libatk1.0-0 i386 2.20.0-1 [58.1 kB]
Get:3 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libgdk-pixbuf2.0-0 i386 2.34.0-1ubuntu2 [171 kB]
Get:4 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libdatrie1 i386 0.2.10-2 [18.8 kB]
Get:5 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libthai0 i386 0.1.25-1 [18.8 kB]
Get:6 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libpango-1.0-0 i386 1.40.1-1ubuntu1 [155 kB]
Get:7 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libgraphite2-3 i386 1.3.8-1ubuntu1 [74.0 kB]
Get:8 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libharfbuzz0b i386 1.2.7-1 [188 kB]
Get:9 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libpangoft2-1.0-0 i386 1.40.1-1ubuntu1 [36.4 kB]
Get:10 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libpangocairo-1.0-0 i386 1.40.1-1ubuntu1 [22.5 kB]
Get:11 http://za.archive.ubuntu.com/ubuntu yakkety-updates/main i386 libgtk2.0-0 i386 2.24.30-4ubuntu3 [1,903 kB]
Get:12 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libnspr4 i386 2:4.12-2ubuntu1 [121 kB]
Get:13 http://za.archive.ubuntu.com/ubuntu yakkety-security/main i386 libnss3 i386 2:3.26.2-0ubuntu0.16.10.1 [1,211 kB]
Get:14 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libice6 i386 2:1.0.9-1 [38.2 kB]
Get:15 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libsm6 i386 2:1.2.2-1 [14.8 kB]
Get:16 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libxt6 i386 1:1.1.5-1 [164 kB]
Get:17 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libxmu6 i386 2:1.1.2-2 [48.4 kB]
Get:18 http://za.archive.ubuntu.com/ubuntu yakkety/main i386 libxaw7 i386 2:1.0.13-1 [182 kB]
Get:19 http://za.archive.ubuntu.com/ubuntu yakkety-updates/main i386 libgail18 i386 2.24.30-4ubuntu3 [15.0 kB]
Get:20 http://za.archive.ubuntu.com/ubuntu yakkety-updates/main i386 libgail-common i386 2.24.30-4ubuntu3 [125 kB]
Fetched 4,596 kB in 10s (449 kB/s)                                             
Selecting previously unselected package libbz2-1.0:i386.
(Reading database ... 296794 files and directories currently installed.)
Preparing to unpack .../00-libbz2-1.0_1.0.6-8build1_i386.deb ...
Unpacking libbz2-1.0:i386 (1.0.6-8build1) ...
Selecting previously unselected package libatk1.0-0:i386.
Preparing to unpack .../01-libatk1.0-0_2.20.0-1_i386.deb ...
Unpacking libatk1.0-0:i386 (2.20.0-1) ...
Selecting previously unselected package libgdk-pixbuf2.0-0:i386.
Preparing to unpack .../02-libgdk-pixbuf2.0-0_2.34.0-1ubuntu2_i386.deb ...
Unpacking libgdk-pixbuf2.0-0:i386 (2.34.0-1ubuntu2) ...
Selecting previously unselected package libdatrie1:i386.
Preparing to unpack .../03-libdatrie1_0.2.10-2_i386.deb ...
Unpacking libdatrie1:i386 (0.2.10-2) ...
Selecting previously unselected package libthai0:i386.
Preparing to unpack .../04-libthai0_0.1.25-1_i386.deb ...
Unpacking libthai0:i386 (0.1.25-1) ...
Selecting previously unselected package libpango-1.0-0:i386.
Preparing to unpack .../05-libpango-1.0-0_1.40.1-1ubuntu1_i386.deb ...
Unpacking libpango-1.0-0:i386 (1.40.1-1ubuntu1) ...
Selecting previously unselected package libgraphite2-3:i386.
Preparing to unpack .../06-libgraphite2-3_1.3.8-1ubuntu1_i386.deb ...
Unpacking libgraphite2-3:i386 (1.3.8-1ubuntu1) ...
Selecting previously unselected package libharfbuzz0b:i386.
Preparing to unpack .../07-libharfbuzz0b_1.2.7-1_i386.deb ...
Unpacking libharfbuzz0b:i386 (1.2.7-1) ...
Selecting previously unselected package libpangoft2-1.0-0:i386.
Preparing to unpack .../08-libpangoft2-1.0-0_1.40.1-1ubuntu1_i386.deb ...
Unpacking libpangoft2-1.0-0:i386 (1.40.1-1ubuntu1) ...
Selecting previously unselected package libpangocairo-1.0-0:i386.
Preparing to unpack .../09-libpangocairo-1.0-0_1.40.1-1ubuntu1_i386.deb ...
Unpacking libpangocairo-1.0-0:i386 (1.40.1-1ubuntu1) ...
Selecting previously unselected package libgtk2.0-0:i386.
Preparing to unpack .../10-libgtk2.0-0_2.24.30-4ubuntu3_i386.deb ...
Unpacking libgtk2.0-0:i386 (2.24.30-4ubuntu3) ...
Selecting previously unselected package libnspr4:i386.
Preparing to unpack .../11-libnspr4_2%3a4.12-2ubuntu1_i386.deb ...
Unpacking libnspr4:i386 (2:4.12-2ubuntu1) ...
Selecting previously unselected package libnss3:i386.
Preparing to unpack .../12-libnss3_2%3a3.26.2-0ubuntu0.16.10.1_i386.deb ...
Unpacking libnss3:i386 (2:3.26.2-0ubuntu0.16.10.1) ...
Selecting previously unselected package libice6:i386.
Preparing to unpack .../13-libice6_2%3a1.0.9-1_i386.deb ...
Unpacking libice6:i386 (2:1.0.9-1) ...
Selecting previously unselected package libsm6:i386.
Preparing to unpack .../14-libsm6_2%3a1.2.2-1_i386.deb ...
Unpacking libsm6:i386 (2:1.2.2-1) ...
Selecting previously unselected package libxt6:i386.
Preparing to unpack .../15-libxt6_1%3a1.1.5-1_i386.deb ...
Unpacking libxt6:i386 (1:1.1.5-1) ...
Selecting previously unselected package libxmu6:i386.
Preparing to unpack .../16-libxmu6_2%3a1.1.2-2_i386.deb ...
Unpacking libxmu6:i386 (2:1.1.2-2) ...
Selecting previously unselected package libxaw7:i386.
Preparing to unpack .../17-libxaw7_2%3a1.0.13-1_i386.deb ...
Unpacking libxaw7:i386 (2:1.0.13-1) ...
Selecting previously unselected package libgail18:i386.
Preparing to unpack .../18-libgail18_2.24.30-4ubuntu3_i386.deb ...
Unpacking libgail18:i386 (2.24.30-4ubuntu3) ...
Selecting previously unselected package libgail-common:i386.
Preparing to unpack .../19-libgail-common_2.24.30-4ubuntu3_i386.deb ...
Unpacking libgail-common:i386 (2.24.30-4ubuntu3) ...
Setting up libgdk-pixbuf2.0-0:i386 (2.34.0-1ubuntu2) ...
Setting up libdatrie1:i386 (0.2.10-2) ...
Setting up libthai0:i386 (0.1.25-1) ...
Setting up libbz2-1.0:i386 (1.0.6-8build1) ...
Setting up libnspr4:i386 (2:4.12-2ubuntu1) ...
Setting up libgraphite2-3:i386 (1.3.8-1ubuntu1) ...
Processing triggers for libc-bin (2.24-3ubuntu2) ...
Setting up libatk1.0-0:i386 (2.20.0-1) ...
Setting up libpango-1.0-0:i386 (1.40.1-1ubuntu1) ...
Setting up libice6:i386 (2:1.0.9-1) ...
Setting up libsm6:i386 (2:1.2.2-1) ...
Setting up libnss3:i386 (2:3.26.2-0ubuntu0.16.10.1) ...
Setting up libharfbuzz0b:i386 (1.2.7-1) ...
Setting up libpangoft2-1.0-0:i386 (1.40.1-1ubuntu1) ...
Setting up libxt6:i386 (1:1.1.5-1) ...
Setting up libpangocairo-1.0-0:i386 (1.40.1-1ubuntu1) ...
Setting up libxmu6:i386 (2:1.1.2-2) ...
Setting up libxaw7:i386 (2:1.0.13-1) ...
Setting up libgtk2.0-0:i386 (2.24.30-4ubuntu3) ...
Setting up libgail18:i386 (2.24.30-4ubuntu3) ...
Setting up adobeair (1:2.6.0.2) ...
Setting up libgail-common:i386 (2.24.30-4ubuntu3) ...
Processing triggers for libc-bin (2.24-3ubuntu2) ... 
```
I did everything Artificial Intelligence said. Does this output look fine.

---

### Post by jsc12345 on 2017-02-15
Okay, Adobe AIR is running! Thanks AI!! :D

---

### Post by jsc12345 on 2017-02-15
Right, I'm bringing this thread back because whenever I try to run a .air file, it goes through the whole installation process and then gives me this error: > Adobe AIR application could not be installed. Debian tools for creating deb packages (such as dpkg-deb or ar) were not found on the system. I'm trying to install the Scratch Offline Editor. What stuff do I need to install? Thanks

---

### Post by vasa1 on 2017-02-15
> **jsc12345 said:**
> Right, I'm bringing this thread back because whenever I try to run a .air file, it goes through the whole installation process and then gives me this error: Adobe AIR application could not be installed. Debian tools for creating deb packages (such as dpkg-deb or ar) were not found on the system. I'm trying to install the Scratch Offline Editor. What stuff do I need to install? Thanks
Unril you're finally satisfied, you can mark the thread [UNSOLVED] just the way you marked it [SOLVED]. You'll see the [UNSOLVED] option now in the Thread Tools dropdown.

---

### Post by jsc12345 on 2017-02-16
Bump

---

### Post by jsc12345 on 2017-02-17
Bump

---

### Post by jsc12345 on 2017-02-17
I'm actually just going  to uninstall adobe air. It's useless, asking for non-existent packages and all that.

---

### Post by Perfect Storm on 2017-02-17
I don't know Scratch Offline Editor but maybe find an alternative instead.

---

