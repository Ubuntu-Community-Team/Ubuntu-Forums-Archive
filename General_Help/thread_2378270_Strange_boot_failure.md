---
title: "Strange boot failure"
date: 2017-11-21
forum: General Help
---

### Post by skippylou on 2017-11-21
I have two HDs in this box:  500GB SATA and 80GB IDE.  Both contain Ubuntu 14.04 LTS and are (rather were) bootable.  Copied some files from the SATA to the IDE yesterday and shut the computer off.  Today I cannot boot from either one.  The BIOS recognizes that they exist.  I put in a live DVD of Ububtu 16.04 LTS.  Did not install but am running with it.  I ran the built in DISKS program and it recognizes the two HDs and the DVD drive but not my floppy (I remember now, this is why I won't upgrade Ubuntu).  Anyway, the DISKS program also shows:

/dev/loop0 1.5GB LOOP DEVICE /cdrom/casper/filesystem.squashfs mounted at /rofs

The "/rofs" is a clickable link which gives me access to my files on the two HD's.  There are only a handful of small files on these HDs which are not backed up but are very important to me.

Question 1.  Can I copy some files to a blank DVD while running the system from a live CD?

Question 2.  What is the best course of action to get my HDs bootable again?

Question 3.  Is it possible to install a package, like fdutils, when running from a live DVD?  If not, is there a simple step-by-step instructions anywhere to mount a floppy and write files to it when running from a live DVD?

I really appreciate any advice.

---

### Post by blackbird34 on 2017-11-23
As far as I know, the answers to  (1) and (3) are Yes (definitely) and Yes (there's a default password for sudo, you'd need to look it up, it"s something very simple, the same as the username i believe). 

As for question 2, have you tried Boot-repair? You probably messed up some files that the system needs to use in order to start up. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

