---
title: "livecd on dvd, boots but ramdisk not writable"
date: 2005-08-22
forum: General Help
---

### Post by jdh2358 on 2005-08-22
I followed the instructions for creating my own livecd at [https://wiki.ubuntu.com//LiveCDCustomizationHowTo](https://wiki.ubuntu.com//LiveCDCustomizationHowTo).  I added a bunch of my own packages, and after everything was compressed, I had a 900+MB iso.

I burned this onto a DVD on a lark and it actually booted.  When I tried to log into the GNOME session, I got an error "your session lasted less than 10 seconds....".  I killed X with CTRL-ALT-1 and went into a terminal session.  There I found I could not write to the ramdisk, eg 

  ls / > test.file

failed with no space on device.

I did a df -k and found the first device
Filesystem                                  1K-blocks   Used          Available  Use% 
/dev/mapper/casper_snapshot   2015824    1954109   0              100% 

what is interesting about this is that Used is less than the total 1K blocks but there are None available.

My general question: is it possible to follow the standard advice at [https://wiki.ubuntu.com//LiveCDCustomizationHowTo](https://wiki.ubuntu.com//LiveCDCustomizationHowTo) and make a bootable DVD > 700MB?

Or, put another way, is there any guidance for making a Hoary bootable DVD?

Thanks,
JDH

---

