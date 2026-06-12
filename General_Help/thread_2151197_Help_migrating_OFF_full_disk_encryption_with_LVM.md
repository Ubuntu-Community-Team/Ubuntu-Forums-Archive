---
title: "Help migrating OFF full disk encryption with LVM?"
date: 2013-06-03
forum: General Help
---

### Post by fitzhugh on 2013-06-03
My goals: get rid of encryption and keep current heavily-tweaked distribution.

I've got three drives: small w/ vanilla partitions, medium w/ lvm, large w/ encrypted lvm. My install is on the encrypted partition w/lvm. I want to move to an empty lvm volume on the other, non-encrypted drive. In the past I've moved installs around by copying and editing grub or lilo. I'm unclear on how to do so with encryption involved (and grub2 confuses me, but that part I can figure out). Can anyone outline the steps or logical path to doing this?
 


Longer version:
I've made a mess of things over the years and am finally attempting to clean it all up. 
A few years ago I got a new 1TB drive and installed a new distro [xubuntu 11.10] on it. It has a tiny  250M boot partition and the rest is a partion containing an encrypted lvm physical volume set up during the install. Silly me, I thought I'd just play with it for a day and go and re-install w/out encryption. Needless to say I never did - until now. 

I've now got three disks:
sda has a tiny partition for /boot and an empty partition I can migrate to (as well as various other paritions)
sdb has a tiny partition for /boot and a large partition containing lvm2 physical volume, including a logical volume I can migrate to (as well as other volumes)
sdc has a tiny partition for /boot and a large encrypted partition containing lvm2 - currently containing my install (including /home - not mounted separately) but no longer containing any vital files outside of /home. I've backed up all files I need, but want to move / off of sdc, format sdc (lvm2, NO encryption) and move it back. I've tweaked my install so much I don't want to start over.

I don't recall which drive has the current MBR (I'll check when I reboot, knowing me, it isn't a given it's on the same disk as the distribution), but you can see above I've installed and reinstalled and moved a bunch and know I can screw it up, hence asking.

I'll take any suggestions or pointers you might have.
Thank you!

---

