---
title: "DVD Shrink - No dvd devices found"
date: 2005-08-19
forum: General Help
---

### Post by Calgarian on 2005-08-19
I am trying to get DVD Shrink to run under wine on my Kubuntu 5.04 system. Everything seems to go correctly except when I execute the program there are no DVD devices found. (The same thing happens for DVD Decrypter). The drop down list is empty when you do an "Open Disc" function. I have read the Ubuntu HowTo, the Ubuntu FAQs, the wine configuration documentation, and the wine FAQs. I've run out of places to try and fix my problem so I hope someone here can give me some guidance. TIA

Here is a bunch of information about my current configuration. I have a Plextor DVD+RW device at /dev/hdc and an HP CD-RW at /dev/hdd. DMA is on for both devices. Both devices work properly under native Kubuntu with K3B and other software.

I made sure that the /fstab file was configured the way the Ubuntu HowTo and the Wine configuration documentation recommends.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>                <dump>  <pass>
proc           /proc           proc    defaults                   0       0
/dev/hda1   /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5   none            swap    sw                         0       0
/dev/hdc     /media/cdrom0   auto    ro,user,noauto,unhide     0   0
/dev/hdd     /media/cdrom1   auto    ro,user,noauto,unhide     0   0
/dev/sda     /media/usb0     auto    rw,user,noauto             0       0

From the Ubuntu How To on DVD Shrink I added the following to my /.wine/config file as recommended.

;; for DVD Shrink - per Ubuntu forums
[Drive D] "Path" = "/media/cdrom0" "Type" = "cdrom" "Label" =                       "CD-Rom" "Filesystem" = "winxp"

;; for DVD Shrink - per Ubuntu howtos
[AppDefaults\\DVD Shrink 3.2.exe\\Version] "Windows" = "winxp"]

In /.wine/doservices/d: there is the symlink that was recommended by the How To. dosdevices/d: has symlink to /media/cdrom0

The basic system is as follows:

Kubuntu - 5.04 (kept current)

wine - 0.0.20050628-1ubuntu1 (installed by synaptic)

DVD Shrink - 3.2 (downloaded as a .zip, expanded and installed from dvdshrink32setup.exe

---

### Post by buldir on 2005-08-19
Try [here](http://www.mrbass.org/linux/ubuntu/dvdshrink/).

---

### Post by Calgarian on 2005-08-21
I tried to do as the How To directed, but winesetup can't be loaded with the current releases of wine. I had tried this prior to posting. There is a conflict issue that I can't determine.

I then went to wine-HQ and got the instructions to load the most current wine and use winecfg. It seemed to work perfectly. I was able to define drives and then install DVD Shrink. However, I still get a blank device list when I execute DVD Shrink. I'll keep trying thigs, but I'm getting pretty frustrated. Can I post any other information to assist in assisting me?

---

### Post by buldir on 2005-08-21
Did you install winesetuptk via synaptic or apt-get?  After installing wine and winesetuptk I typed in the terminal:

```
wine
``` 

to set up the .wine home directory, then ran:

```
winesetup
``` 

to create the .config file.  The only changes I made in the .config were in the section:

```
# [wineconf]

[Version]
; Windows version to imitate (win95,win98,winme,nt351,nt40,win2k,winxp,win2k3,win20,win30,win31)
"Windows" = "winxp"
; DOS version to imitate
"DOS" = "6.22"
```

So the changes I made were "Windows" = "winxp" and "DOS" = "6.22" (by removing the semicolon, ;, in front of "DOS" = "6.22".  I didn't muck with anything else.  Try it again.  If this doesn't work, try changing the D drive symlink to /dev/hdc instead of /media/cdrom0.

---

### Post by Calgarian on 2005-08-21
I had tried both apt-get and synaptic for the wine winesetuptk install. I got a reject on incompatability both ways. So I cleaned out everything related to DVD Shrink and wine and went to wine-hq and added them to the repository. This got me version 0.0.20050725-winehq-1. This version uses winecfg and doesn't have a config file. Supposedly everything is in the registry. With winecfg I appear to get all my devices found and registered. Then I reinstalled DVD Shrink and it appeared clean. Execution once again gives an empty device list. I'm going to try the link to /dev/hdc instead of /media/cdrom0.

---

### Post by buldir on 2005-08-21
That's really wierd.  If I remember right, I installed wine and winesetuptk via synaptic without any problems.  I do have an older version of wine (as .deb) that may work better for you, but my ftp site is currently down.

---

### Post by bionnaki on 2005-08-21
[http://yousendit.com](http://yousendit.com)
& just post the link
(leave the email part blank)

I could use this as well.

Thanks!

---

### Post by buldir on 2005-08-22
Here's the link to the 20050111 Wine .deb...I used another webftp service.  Yousendit.com was very, very slow uploading the file.  Get it while it's hot...the link is good for 72 hrs.

[wine_0.20050111-2_i386.deb](http://www4.sendthisfile.com/d.jsp?t=GGeAgYU6JV5O1xe7hnGERJM9)

---

### Post by Calgarian on 2005-08-24
I have made some progress now. If I issue an explicit mount /dev/hdc in a terminal window I now get the device "D:\movie_name" in the devices list when I do an "open disc." If I select that item from the list and press OK I get an error message:

DVD Shrink encountered an error and cannot continue.
Failed to read file "D:\"

Now I'm stuck again. Any other thoughts on this issue?

By the way I'm still using the latest Wine-HQ 725 release with winecfg. If I can't get that to work in the next day or so I'll drop back to an older wine and winesetuptk and try that. One would think that the newer wine should be better?

---

