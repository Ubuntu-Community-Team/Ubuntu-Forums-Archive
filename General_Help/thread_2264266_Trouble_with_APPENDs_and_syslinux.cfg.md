---
title: "Trouble with APPENDs and syslinux.cfg"
date: 2015-02-06
forum: General Help
---

### Post by Chetyre on 2015-02-06
While playing around with a new flash drive, I decided I wanted to make a nice multi-boot stick.  To test the waters, I used the tool Multiboot USB to put Ubuntu and UBCD on the same stick and it worked fine.  The next step I wanted to try was adding persistence to my Ubuntu disc, so I downloaded PDL Casper-RW Creator.  I generated a 4GB blank casper-rw file and dropped it in the root of the drive.

Next, I went into my syslinux.cfg to add in my boot options.  Unfortunately, nothing seems to apply.  I put in options for persistence and to skip the Try/Install screen and neither is working.  Otherwise it boots fine.  Does anyone have any ideas?  I am pretty new to this.

This is what the relevant section of my syslinux.cfg looks like--
```
#start ubcd533
LABEL ubcd533
MENU LABEL ^UBCD
BOOT /multibootusb/ubcd533/boot/syslinux/ubcd.bs
#end ubcd533

#start ubuntu-14.04.1-desktop-amd64
LABEL ubuntu-14.04.1-desktop-amd64
MENU LABEL U^buntu
BOOT /multibootusb/ubuntu-14.04.1-desktop-amd64/isolinux/ubuntu.bs
APPEND persistent quiet splash noprompt --
#end ubuntu-14.04.1-desktop-amd64

```

---

