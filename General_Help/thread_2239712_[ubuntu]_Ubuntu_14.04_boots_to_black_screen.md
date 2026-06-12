---
title: "[ubuntu] Ubuntu 14.04 boots to black screen?"
date: 2014-08-15
forum: General Help
---

### Post by sports fan Matt on 2014-08-15
So I get up and turn on my laptop this morning and it instantly boots up to a black screen. The cursor is there but frozen (so it appears) so I can't perform a ctrl>alt>F1. How can i check to 
see if all the files are intact so I don't have to reinstall W7 and 12.04?

I'm actually kind of doing that as we speak. I'm using the last of my hard drive to create a fresh 12.04 install can I do the same instructions with that?  I would assume so

Using Gparted I deleted the unusable 14.04 partition which was on sda3. How can i re allocate that space to split my partitions in half so they aarer pretty much equal Windows and Ubuntu?

I'm trying to figure out if I can fix this within Ubuntu or if I need to boot into Windows for this fix.

---

### Post by sports fan Matt on 2014-08-15
I booted over to Windows and this is my result.  So my question is which is easier? taking partition 5 or 7 and expanding it or using SDA 2 and using windows to resize to get almost equal between Windows and Ubuntu by moving and resizing SDA3. Just not sure..partitioning is not my strong suit

---

### Post by yancek on 2014-08-15
> Using Gparted I deleted the unusable 14.04 partition which was on sda3.

Your GParted output shows sda3 as an Exteneded partition.  An Extended partition is a primary partition used as a container for logical partitions.  An Extended partition cannot contain data or filesystems but logical partitions can.  Your output shows sda7 as the / (root) partition which is where I expect you have/had Ubuntu installed.  On this Extended partition you have sda5 (data?), sda6 swap and sda7 the Ubuntu system.

Your windows partitions (sda1 and sda2) have a combined size equal to that of the Extended partition which contains the logical partitions with Ubuntu.  Nothing to do.

I'm not sure what you are trying to fix.  The boot to a black screen?  Did you make any changes or do any updates before you first noted this problem?  These things don't just happen unless you are having some kind of hardware failure and this doesn't seem like hardware.

If you are reinstalling Ubuntu 12.04, it would probably be best to install it to sda7.

---

