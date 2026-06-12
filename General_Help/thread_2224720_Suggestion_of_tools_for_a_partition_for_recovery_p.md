---
title: "Suggestion of tools for a partition for recovery purposes"
date: 2014-05-17
forum: General Help
---

### Post by colinzealknows on 2014-05-17
Hi guys,

Every now and then I have to load some recovery tool on my USB - GParted, Clonezilla, boot-repair, etc.

I was thinking I would create a partition that had these things already loaded, so it would save me that trouble.

Is there any readymade list of these small and incredibly useful applications? or maybe a whole bootable application with all these tools already loaded into it so I can just create a partition with it? It's hard to Google it; "linux recovery partition" brings a lot of stuff about how to recover partitions and such.

Thanks.

---

### Post by Mark Phelps on 2014-05-17
These tools exist in two different forms -- applications and LiveCDs.  Having the first on another partition would not only do little good, since it's really HARD to install apps to other than their native location, it would be very difficult to do.

As to the second, all of them can be saved in ISO form in another partition and then be booted from the GRUB menu.  I have GParted, Clonezilla, and RedoBackup all saved this way and can boot into any of them when I need to do stuff.  Each of these has instructions on how to do this on their respective websites.

---

### Post by colinzealknows on 2014-05-17
Geez, turns out that they have instructions for that.

So you have one small partition for each of those things? Interesting.

Any other tool you think it's valuable? I haven't heard of RedoBackup before.

Thanks for the heads up.

---

### Post by Mark Phelps on 2014-05-17
I don't have a separate partition, instead, I have a folder named "isos" in the "boot" folder of my Ubuntu installation. In there is the most current ISO file for each of the three" Clonezilla, GParted, RedoBackup.

I also have a Custom_41 GRUB stanza file containing boot instructions for each of the three ISOs.  A good place to see what needs to be in this is the Clonezilla website where they have a faq about being able to boot from an ISO on your hard drive.

Getting this working involves some trial-and-error and a LOT of reading to figure out how to do it.

An easier approach is to have a LiveUSB of each of these.  You can then stick in the USB stick you want, boot from it, and run the utility.

---

### Post by sammiev on 2014-05-17
I put all those utilities on a one bootable USB where you just select the one you want on boot.

---

### Post by oldfred on 2014-05-18
I do this on my hard drive and it is somewhat similar on a flash drive.
 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

With a smaller flash drive I just install grub to it and manually create grub.cfg with correct boot stanza. Similar to examples above for hard drive.
If a larger flash drive, I put a full install of Ubuntu, Kubuntu or Lubuntu on flash drive and use the hard drive example above to add many repair ISO.

I have a few ISO on hard drive, and only put some on each flash drive, I edited out most of Ubuntu ISO

```
fred@fred-Precise:/media/MavData/iso$ cat livecdimage.cfg  | grep menuentry
# menuentry 'Live ISOs' {
menuentry "Ubuntu 14.04 Trusty ISO 64bit" {
menuentry "Ubuntu 14.10 Utopic ISO 64bit Daily" {
menuentry "Ubuntu 14.10 Utopic Lubuntu ISO 64bit Daily" {
menuentry "" {
menuentry "Boot-Repair Disk ISO 64bit" {
menuentry "Ubuntu 12.04 Secure Remix ISO 64bit" {
menuentry "Ubuntu 12.04 Precise mini ISO 64bit" {
menuentry "" {
menuentry "Parted Magic 2013 (Boot ISO Image via Grub2) " {
menuentry "gparted 0.16 (Boot ISO Image via Grub2) " {
menuentry "Boot-Repair ISO 64bit " {
menuentry "Rescatux" {
menuentry "SystemRescue CD on hard drive" {
menuentry "super_grub2_disk_hybrid_2.00 " {
menuentry "Reboot" {
menuentry "Halt" {

```

---

### Post by stalkingwolf on 2014-05-18
you might check out Hirens.  that disc has many tools for everything from virus scans to hdd repair to cloning.

just fwiw i have all of my tools on 2gb flash drives.

---

