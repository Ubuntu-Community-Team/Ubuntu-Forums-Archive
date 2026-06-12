---
title: "Installing Epson 4490 Photo Scanner"
date: 2008-05-05
forum: General Help
---

### Post by edson.costa on 2008-05-05
I am unable to install my scanner neither on 8.04 or any other previous versions.

Xsane returns a no device available message.

I have been look around and none of the suggestions found on the forum worked at all.

This is the only thing missing to get out of Windows completely.

Any help will be more then welcome. I am lost!

Edson:

---

### Post by warp99 on 2008-05-05
Epson has their own driver for that model located here:

[http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/scan/DL1.do)

Download the package for 'Debian' and install by right clicking on the file and using gdebi or open a terminal, go to the directory of the file, then:

```
sudo dpkg -i <name_of_package>.deb
```

You may need to use the '--force-overwrite' parameter since one of the files may conflict with another package. So your string would look like this:
```
sudo dpkg --force-overwrite -i <name_of_package>.deb
```

---

### Post by edson.costa on 2008-05-05
I have done this before. There is only rpm and tar files on this site. I use alien to convert them and:

Tar file result in a good conversion to debian but it reults in sucessfull instalation and doesn't work

tehre are 2 RPM files one converts fine. However the plugin file converts in a non installable directory instead.

---

### Post by rbmorse on 2008-05-06
I just tried this and the .rpm conversion for the plugin failed for me as well. It worked fine with Gutsy so the problem might be something that changed in Hardy. 

Investigating.

---

### Post by rbmorse on 2008-05-06
YOu might be in luck.  When I tried to convert the plugin .rpm the process failed, leaving a folder on my desktop instead of a finished .deb file. 

Open that folder and navigate to /usr/share/iscan. Do you see a file named esfw54.bin of 64.3Kb size?

Now...on my system with a working 4490, I happen to have a 64.3Kb file named /usr/share/iscan/effw54.bin with owner root, group root, and owner read/write, group read and others read permissions set.   

So, what I would try is to install the .deb that did convert (the iScan program) using dpkg as indicated in the earlier post, and then manually copy esfw54.bin to the /usr/share/iscan folder and set permissions accordingly.    

Then, in the same folder that resulted from the failed .rpm conversion, check the usr/lib/iscan folder.  I found two shortcuts and the 227.9Kb file libesint54.so.2.0.0  

My live installation has those same shortcuts and then libesint54.so.2.0.0 file installed at /usr/lib/iscan so copy those to /usr/lib/iscan/ on your system, too. 

One last thing to check. Installing the iscan program may have created the file /etc/udev/rules.d/60_iscan.rules. If so, fine.  If not copy the following into a new file named /etc/udev/rules.d/60_iscan.rules 
```

# This file is part of the "Image Scan! for Linux" binary package (or
# generated automatically as part of its installation).  Any changes
# will be overwritten with each upgrade of the package.

ACTION!="add", GOTO="iscan_rules_end"
SUBSYSTEM!="usb_device", GOTO="iscan_rules_end"

SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0101", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0103", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0104", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0106", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0107", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0109", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="010a", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="010b", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="010c", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="010e", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="010f", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0110", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0112", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0116", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0118", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0119", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="011b", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="011c", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="011d", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="011e", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0121", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0122", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0126", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0128", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0129", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012a", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012b", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012c", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012d", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012e", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="012f", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0801", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0802", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0805", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0806", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0807", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="080d", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="080e", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="080f", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0810", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0811", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0813", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0814", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0815", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0817", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0818", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0819", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="081a", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="081c", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="081d", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="081f", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0820", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0827", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0828", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0829", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082a", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082b", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082e", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082f", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0830", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0833", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0835", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0836", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0837", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0838", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0839", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083a", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083c", MODE="0666"
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="083f", MODE="0666"

LABEL="iscan_rules_end"

```

With luck, the iscan program installer does all the fixups and path assignments and the plugin .rpm just installs the proprietary binary blob, so it might just work.  Or, it will be easy to undo if it doesn't...just go back and remove all the things you just installed.

---

### Post by rbmorse on 2008-05-06
Here's the filelist taken from a successful .deb conversion of the GT-750 plugin .rpm.
```
./
usr/
usr/share/
usr/share/iscan/
usr/share/iscan/esfw54.bin
usr/share/doc/
usr/share/doc/iscan-plugin-gt-x750/
usr/share/doc/iscan-plugin-gt-x750/copyright
usr/share/doc/iscan-plugin-gt-x750/changelog.Debian.gz
usr/share/doc/iscan-plugin-gt-x750-1.0.0/
usr/share/doc/iscan-plugin-gt-x750-1.0.0/EAPL.en.txt
usr/share/doc/iscan-plugin-gt-x750-1.0.0/EAPL.ja.txt
usr/lib/
usr/lib/iscan/
usr/lib/iscan/libesint54.so.2.0.0
usr/lib/iscan/libesint54.so
usr/lib/iscan/libesint54.so.2
```
I haven't done a file by file check, but it looks like these are all present in the failed .rpm converion folder, so if you want to do all of the files in the package this is where they would go on your system.

---

### Post by Dai777 on 2008-05-06
[http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

sudo alien -k pipslite-cups-1.0.3-1.i386.rpm
sudo alien -k iscan_2.11.0-1.c2_i386


usr/share/cups/model/eklite.ppd

see video advice for printer:
[http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html](http://dai-videotutes.blogspot.com/2008/05/installing-epson-dx8400-on-ubuntu.html)

========================================================================
Install both debs for printer and scanner then do the following to get the scanner working.
1.Make sure that scanning users are added to group scanner
2. Edit sudo gedit /etc/sane.d/epkowa.conf
add:
usb 0x04b8 0x0839

and commented out:
SCSI EPSON

3. Edit sudo gedit /etc/udev/rules.d/45-libsane.rules
Add:
# Epson DX-8400
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="0839", MODE="664", GROUP="scanner"

Reboot and all is well.. Kooka, xsane, and everything else works swimmingly.

2.If you can't get scanner to work check for the following files
3.sudo gedit /etc/sane.d/epson.conf
4.sudo gedit /etc/sane.d/epson2.conf
5.add:
usb 0x04b8 0x0839
6.and commented out:
SCSI EPSON



usb 0x04b8 0x0839 you will have to find the vendor and product id to suit your printer theses are for the dx8400

---

### Post by rbmorse on 2008-05-06
Dia777, while your post is consistent with what it took to get an Epson GT-750/Perfection 4490 Color scanner requiring an Avasys proprietary binary driver working under earlier versions of Ubuntu (specifically 7.10), none of that should be necessary for the 4490 under Ubuntu 8.04 (Hardy). 

All you should have to do in Hardy is install SANE and it's support packages, download the .rpms of the iscan application and the proprietary binary blobs in the plugin from Avasys, convert the .rpm files to .deb files with Alien, install the two .deb files and the scanner should just work. 

The problem edson.costa and I share is that under Hardy, the GT-750 plugin .rpm from the Avasys site containing the proprietary binaries does not successfully convert using Alien (the first step in your message).  

I'm hoping that running the Iscan installer (which does convert) will be enough to allow one to simply copy the driver blob, interface library and other files created from the plugin .rpm by Alien before it fails into place on the target system.  

I can't (chose not to) test it myself because I still had the iscan and plugin .debs created under Gutsy and used those to get my 4490 working. I do not want to mess that up. 

Also note:

Your step 2. The version of the sane-epkowa backend included with 8.04 already supports the Epson Perfection 4490 color scanner (although not your DX-8400), so it is no longer necessary to edit the file /etc/sane.d/epkowa.conf to gain SANE support for the GT-750/Perfection 4490 Color. 

Your step 3. My Hardy installation does not have the file /etc/udev/rules.d/45-libsane.rules. It does have /etc/udev/rules.d/60_iscan.rules which should be generated by the iscan installer. 60_iscan.rules  includes support for your product 0839 well as for product 0119, the model 4490. 

Including (or adding) the 45-libsane.rules line with the proper product ID is no doubt is harmless as it has a higher priority than the 60_iscan.rules file, but it's probably not necessary anymore, either. Note that 60_iscan.rules sets the permissions for all included devices to 0666.

---

### Post by Ralphie on 2008-05-21
rbmorse, would your .deb files work on other peoples systems? 
If so, I would gladly host them on my webspace, I can provide you with my information to get them up. 

Simply moving the files over did not work for me.

---

### Post by Ralphie on 2008-05-22
Alright so I actually found a .deb that I converted a while back sitting on an old hard drive, I've attached both files necessarry in .deb form so that you guys no longer have to convert them.

[I]**Moderator note:** There may be a licensing/redistribution issue with the Avasys drivers. Attachments have been removed; drivers should be downloadable in deb form by selecting Debian when downloading.
[http://avasys.jp/hp/menu000000500/hpg000000442.htm](http://avasys.jp/hp/menu000000500/hpg000000442.htm)
--**jacobmp92**[/I]

I was having trouble getting it to work at first, but managed to get it to work after installing libsane-extras, so here is my little tutorial:

-------------------------------------------------------------
**1. Install / make sure you have all of these packages installed:**

libsane
sane-utils
xsane
xsane-common
libsane-extras

**2. Download my attached .deb files, and install them like so:**
cd to their directory in the terminal, then enter:
```
sudo dpkg --force-overwrite -i iscan-plugin-gt-x750_1.0.0-2_i386.deb
```
and
```
sudo dpkg --force-overwrite -i iscan_2.10.0-2_i386.deb
```

**3. Run it by opening a terminal and typing**
```
iscan
```
or you can use 
```
xsane
``` 
-- whichever's clever.

---

### Post by Ralphie on 2008-05-23
jacobmp92, All that is given are .rpm's which no longer convert properly using alien under 8.04

The frustrating part is AVASYS Corporation does not provide an email address or anything for me to send my converted files to so that they can actually provide a proper .deb package...
hmmm

---

