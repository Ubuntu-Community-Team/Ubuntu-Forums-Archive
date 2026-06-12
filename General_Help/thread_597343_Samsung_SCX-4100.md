---
title: "Samsung SCX-4100"
date: 2007-10-30
forum: General Help
---

### Post by New to Linux on 2007-10-30
I'm having trouble configuring my scx-4100 printer.  I changed the install and setup scripts to use bashs, and added  update permissions, but the installed drivers will not work.  (I believe the install pretty much runs with out any errors)

The installation routine does INSTALL the printer (and the device manager to the desktop), and it will UNINSTALL them as well.  They just don't work.  I've tried to install _with and without_ the CUPS and SANE drivers, which made no difference.

I noticed in the install.sh script that there is no platform for Ubuntu (there is for red hat, fedora,suse, etc), so it uses the 'OTHER' platform configuration option.

Any idea what is causing the problem I'm having ?  Besides me of course !   Anyone with a work around ?

---

### Post by lattmau on 2007-10-30
not sure if this answers your question, but i followed this

[http://www.elijahlofgren.com/linux/ubuntu/#scx-4100](http://www.elijahlofgren.com/linux/ubuntu/#scx-4100)

couldnt get the scanner working quite right though. it would crash when i try to scan something in openoffice

---

### Post by New to Linux on 2007-10-30
Thanks ! Idon't think I've seen this -  I don't recall the section for ubuntu.  Are you  using a USB printer cable ?

---

### Post by lattmau on 2007-10-30
Yeah, I'm using USB cable.  

Just a heads up though, I think when that guy wrote that guide, he was using a older driver from the Samsung page.  So not all the steps match 100%, but gives you a gist.  I was going to email him about the scanner question, but never got around to it.  Let me know how yours goes.

I actually need to reinstall the printer too because I recently did a clean install of ubuntu.

---

### Post by New to Linux on 2007-10-30
Thanks for the heads up lattmau, I'll let you know how it turns out. 
R

---

### Post by New to Linux on 2007-10-30
lattmau,

I used this install for the printer and it worked !  (using Ubuntu 7.10)
The GUI interface is pretty good, and the configurator works good too.

However, the scanner is not recognized. The Samsung manual does not help with this either. It does not show up as a scanner device on the configuration utility. 

Looks like we have more work to do.

Thanks a bunch for your help !

---

### Post by New to Linux on 2007-11-05
3 more days of trying to get the scanner to be recognized - no luck. I've followed every change (twice) to add it to the link and device libraries, but I think its the SamSung driver that is the problem - the Unified Driver Configurator software doesn't recognize the scanner either !

---

### Post by cburkey on 2007-11-08
I got the scanner working as well.

Just had comment out both lp0 aliases since they are in conflict. 

/etc/udev/rules.d/60-symlinks.rules

# This file establishes user-friendly symlinks to devices according to
# Ubuntu policy.  See udev(7) for syntax.
#
# The names of the actual devices themselves must not be set here, but
# in 20-names.rules; the permissions and ownership of those devices
# should be set in 40-permissions.rules.

# Compatibility symlinks for /dev/scd* devices
SUBSYSTEMS=="scsi", KERNEL=="sr[0-9]*",    SYMLINK+="%k"

# Compatibility symlinks for USB printers
#####This causes a conflict. I think Edgy already creates this symlink
#####SUBSYSTEMS=="usb", KERNEL=="lp[0-9]*",  SYMLINK+="usb%k"

# Create /dev/pilot symlink for Palm Pilots
KERNEL=="ttyUSB*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", \
                    SYMLINK+="pilot"

# Create symlink for usb printer to /dev/usb/lp*
#####This causes a conflict. I think Edgy already creates this symlink
######BUS=="usb", KERNEL=="lp[0-9]*",         SYMLINK+="usb/%k"

---

### Post by New to Linux on 2007-11-09
Thanks for the advice.  

One question - Before you made this fix, did samsung, xsane, gimp, or open office even detect a scanner device ? (mine is not detected at all)

---

### Post by cburkey on 2007-11-09
Yes I had the same problem you had. 

Basically, the installation steps are wrong. Because of the udev legacy printer support it is keeping the latest SCX-4100 drivers from working automatically.

Once you make the change do this:

rm /dev/usb/*
rm /dev/usblp0

sudo /etc/init.d/udev restart

Or just reboot.

Then you can run xsane as root and it will find it.

Another good thing is that USB will auto detect your printer now. So you can delete the old printer left over by the installation.

My changes should be checked into the Ubuntu distribution. They should also add the SCX printer to the list of devices.

---

### Post by New to Linux on 2007-11-09
That's sounds encouraging.

I hate to be a pest ... but it would benefit a lot of people out there (including myself)  if you would provide a step by step guide for installing the linux unified drivers and applying the patches to make this device work.

Then if  the Ubuntu folks will get on board and (add this driver to their package) ...

Thanks a bunch !

---

### Post by cburkey on 2007-11-09
Ok but first let me know if this work:

1. Plug in scanner via USB
2. Make the changes as indicated
3. Reboot
4. Run sudo xsane
5. Tell me if it find it.

---

### Post by jdeperi on 2008-06-27
> **cburkey said:**
> Ok but first let me know if this work:

1. Plug in scanner via USB
2. Make the changes as indicated
3. Reboot
4. Run sudo xsane
5. Tell me if it find it.
I tried steps 1-4, but still received the message "no devices available". Actually, I tried "sudo xsane" both with AND without the aforementioned lines commented out. In either case, after restarting xsane failed to recognize the scanner.

---

