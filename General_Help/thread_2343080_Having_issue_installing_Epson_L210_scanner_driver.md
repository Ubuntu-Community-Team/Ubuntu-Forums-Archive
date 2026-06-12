---
title: "Having issue installing Epson L210 scanner driver"
date: 2016-11-12
forum: General Help
---

### Post by Qualtrough on 2016-11-12
I have upgraded to 16.04 and can use the print functions of my Epson L210 without any problem. 
Xsane does not find a scanner, and I understand that I need to install an iScan scanner driver package from Epson

I have downloaded the scanner driver package deb file from Epson.

When I right click and select Open in Terminal and then paste $ sudo ./install.sh and hit Enter I get the following message which indicate errors:

I have been using Ubuntu for a long time but am not that familiar with code, etc. so if anyone has any suggestions on what to do please bear that in mind. Thanks in advance for any assistance.


```
jb@jb-ThinkCentre-M52:~/iscan-bundle-1.0.3.x86.deb$ sudo ./install.sh
[sudo] password for jb: 
(Reading database ... 217126 files and directories currently installed.)
Preparing to unpack ./core/iscan_2.30.3-1_i386.deb ...
Unpacking iscan:i386 (2.30.3-1) over (2.30.3-1) ...
Preparing to unpack .../iscan-data_1.38.0-1_all.deb ...
Unpacking iscan-data (1.38.0-1) over (1.38.0-1) ...
Preparing to unpack .../iscan-network-nt_1.1.1-1_i386.deb ...
Unpacking iscan-network-nt:i386 (1.1.1-1) over (1.1.1-1) ...
dpkg: dependency problems prevent configuration of iscan:i386:
 iscan:i386 depends on iscan-data.
 iscan:i386 depends on libgtk2.0-0 (>= 2.12.0).
 iscan:i386 depends on libltdl7 (>= 2.2.6b).
 iscan:i386 depends on libsane (>= 1.0.11-3).
 iscan:i386 depends on libusb-1.0-0 (>= 2:1.0.6).


dpkg: error processing package iscan:i386 (--install):
 dependency problems - leaving unconfigured
Setting up iscan-data (1.38.0-1) ...
dpkg: dependency problems prevent configuration of iscan-network-nt:i386:
 iscan-network-nt:i386 depends on iscan (>= 2.29.3); however:
  Package iscan:i386 is not configured yet.


dpkg: error processing package iscan-network-nt:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Processing triggers for udev (229-4ubuntu12) ...
Errors were encountered while processing:
 iscan:i386
 iscan-network-nt:i386
jb@jb-ThinkCentre-M52:~/iscan-bundle-1.0.3.x86.deb$ 



```


UPDATE:  I have extracted the iscan-bundle-1.0.3.x86.deb file in my download folder, and then clicked Open in Terminal. After that I enter  # ./install.sh and get nothing.****This is following the instructions on this page: [http://download.ebz.epson.net/man/linux/iscan_e.html#sec6-1](http://download.ebz.epson.net/man/linux/iscan_e.html#sec6-1)

---

### Post by Qualtrough on 2016-11-13
I have successfully configured my Epson L210 Printer/Scanner to print, but cannot scan as the scanner driver software needs to be installed.

In order to do that I have followed the instructions in this previous post:

[http://askubuntu.com/questions/724323/how-to-install-epson-l210-scanner](http://askubuntu.com/questions/724323/how-to-install-epson-l210-scanner)

I have a 64 bit machine so I changed the command accordingly.

Here is what I get:

```
jb@jb-ThinkCentre-M52:~/iscan-bundle-1.0.3.x64.deb$ sudo ./install.sh[sudo] password for jb: 
Selecting previously unselected package iscan.
(Reading database ... 219521 files and directories currently installed.)
Preparing to unpack .../core/iscan_2.30.3-1_amd64.deb ...
Unpacking iscan (2.30.3-1) ...
Preparing to unpack .../iscan-data_1.38.0-1_all.deb ...
Unpacking iscan-data (1.38.0-1) over (1.36.0-1) ...
Selecting previously unselected package iscan-network-nt.
Preparing to unpack .../iscan-network-nt_1.1.1-1_amd64.deb ...
Unpacking iscan-network-nt (1.1.1-1) ...
Setting up iscan-data (1.38.0-1) ...
Setting up iscan (2.30.3-1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for menu (2.1.47ubuntu1) ...
Setting up iscan-network-nt (1.1.1-1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for udev (229-4ubuntu12) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
jb@jb-ThinkCentre-M52:~/iscan-bundle-1.0.3.x64.deb$ 



```

When I select the XSANE scanner button it can't find a scanner. 

If anyone has any suggestions as to what I am doing wrong I would appreciate it. Although I have been using Ubuntu for more than five years I am not a coder so step by step instructions would be appreciated, thanks.

---

### Post by QIII on 2016-11-14
Threads merged.

Hello!

It will be a lot easier for folks to follow this with both posts in the same thread.

Good luck!

---

### Post by Qualtrough on 2016-11-14
Thanks.

---

### Post by Qualtrough on 2016-11-14
Anyone?

---

### Post by hkhmjar on 2016-12-12
> **Qualtrough said:**
> Anyone?


[https://www.linuxliteos.com/forums/printing-and-scanning/can't-get-epson-l210-scanner-to-work-in-ll-3-2/?topicseen](https://www.linuxliteos.com/forums/printing-and-scanning/can't-get-epson-l210-scanner-to-work-in-ll-3-2/?topicseen)

Happy Trails, Rok

---

### Post by oldrocker99 on 2016-12-12
If you open the file (if it's a .deb file) with Gdebi, it should pull in the dependencies automagically.

---

