---
title: "VirtualBox USB probelms with Hardy Heron"
date: 2008-05-02
forum: General Help
---

### Post by awisur on 2008-05-02
Ok, so I think I've tried everything to get USB to work within VirtualBox in 8.0.4

I use Hardy Heron as host and run  Windows XP pro SP2 as guest inside VB.


Here is a list of things I have done and Still have not seen any result, og seen the least bit of USB in the settings in VB...

So what have i done so far..

I've created the groups 'usbfs' and 'usbusers' and added myself and root to both.

I've edited the file:

/etc/init.d/mountdevsubfs.sh

From:

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs «» /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

To:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs «» /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

This is a Gutsy Gibbon fix, but it was at least commented out in Heron aswell. In addition to this I've edited the file:

/etc/fstab

I've added this line after i checked that the group Number/ID of 'usbfs' was 1002

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

I've rebooted after all this, and I've searched hours on the net for a solution for this.

I really need this to work so all help is greatly appreciated!

Cheers and thanks!

---

### Post by awisur on 2008-05-02
Btw I use VirtualBox 1.5.6...

---

### Post by MattBD on 2008-05-02
I believe the open source version of VirtualBox doesn't support USB connections at all. If you need USB support, I recommend you look at the website, they have a closed-source version which includes an Ubuntu package, and this is free for personal use.

---

### Post by awisur on 2008-05-03
RESOLVED, needed the Closed Source one. Heaps thanks MattBD! Also got webcam to work with skyoe inside VirtualBox :D Also sound with mic :)

---

### Post by schlox on 2008-05-03
> **awisur said:**
> Ok, so I think I've tried everything to get USB to work within VirtualBox in 8.0.4

I use Hardy Heron as host and run  Windows XP pro SP2 as guest inside VB.


Here is a list of things I have done and Still have not seen any result, og seen the least bit of USB in the settings in VB...

So what have i done so far..

I've created the groups 'usbfs' and 'usbusers' and added myself and root to both.

I've edited the file:

/etc/init.d/mountdevsubfs.sh

From:

#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs «» /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb

To:

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs «» /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

This is a Gutsy Gibbon fix, but it was at least commented out in Heron aswell. In addition to this I've edited the file:

/etc/fstab

I've added this line after i checked that the group Number/ID of 'usbfs' was 1002

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

I've rebooted after all this, and I've searched hours on the net for a solution for this.

I really need this to work so all help is greatly appreciated!

Cheers and thanks!

You have written what I was about to write but I was so lazy to sum all up. I did everything you have done, still wasn't able to make it running. Now I will try this closed version. And want to see whether it works...

---

### Post by schlox on 2008-05-03
I think I have looked every single corner of the webpage of virtual box but I still have no clue where this closed source version download link is! Thus I still can't use any usb port!!!

Any comments/feedback?


btw, I am using Hardy 8.04

---

### Post by MattBD on 2008-05-03
It's at [https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)
Use the pulldown box to select the Ubuntu 8.04 version you want. It's now hosted by Sun as they recently bought Innotek, who create VirtualBox.

---

