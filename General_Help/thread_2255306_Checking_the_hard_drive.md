---
title: "Checking the hard drive ?"
date: 2014-12-04
forum: General Help
---

### Post by oygle on 2014-12-04
There used to be a hard disk drive display with other versions of Kubuntu ? I'm getting freezes and the hard drive has been making noises lately. So I'd like to run SMART or whatever it is called. 

I tried using the search in Muon for "disk" or smartmon" and nothing was found.

What is a very good/relaible tool to use in *ubuntu for checking the hard drive ?

Another (related) issue. With previous versions of *ubuntu, every now and then on boot, it would do a disk check. Haven't seen that at all with 14.04

Oygle

---

### Post by dragonfly41 on 2014-12-04
GSmartControl is one tool found in Ubuntu Software Centre.

---

### Post by timgood on 2014-12-04
Search for 'partition' and you will find KDE Partition Manager pre-installed. You can force a disk check by running```
sudo touch /forcefsck
``` in a terminal. The filesystem will be automatically checked on reboot. Hope this helps.

---

### Post by oldos2er on 2014-12-04
> **oygle said:**
> There used to be a hard disk drive display with other versions of Kubuntu ? I'm getting freezes and the hard drive has been making noises lately. So I'd like to run SMART or whatever it is called. 

I tried using the search in Muon for "disk" or smartmon" and nothing was found.

The correct package name is *smartmontools*. [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by oygle on 2014-12-05
Thanks for your help. Have installed smartmontools and GSmartControl	. Ran the 2 short tests, no errors found. Will run the longer test (2 hrs) soon.

---

### Post by oygle on 2015-01-02
Longer test was fine. HDD seems to be okay, no errors. It is 6 years old though; need to replace it.

---

### Post by ron-smith on 2015-01-31
I tried [FONT=courier new]sudo touch /forcefsck[/FONT] and it didn't seem to do anything. Still says *** /dev/xvda1 should be checked for errors *** when I first log in.
I also tried [FONT=courier new]sudo tune2fs -C 50 /dev/xvda1[/FONT] to force it over the boot count and that didn't work either.
Any other suggestions?

---

