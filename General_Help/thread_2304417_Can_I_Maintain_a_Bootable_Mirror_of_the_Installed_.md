---
title: "Can I Maintain a Bootable Mirror of the Installed Drive on an Internal Disk?"
date: 2015-11-26
forum: General Help
---

### Post by buzzingrobot on 2015-11-26
Assume a machine has two identical drives installed and that Drive One is the boot drive and also holds everything else.  How do I create and maintain an up-to-date bootable duplicate of Drive One on Drive Two?

Requirements:

1. No compressed archives, etc.  Just maintain Drive Two as an exact copy of Drive One: Same permissions, attributes, etc.

2. Drive Two should boot when selected in the BIOS without editing fstab.

3. After booting from Drive Two and repairing Drive one, reselect Drive One in BIOS, reboot, and continue maintaining Drive Two as an updated mirror of Drive One.

4. What about kernel updates?  Would I need to manually update grub on Drive Two? Ditto drivers.

Assume Drive One will be a clean install. 

Does filesystem choice play here?  Can btrfs do this kind of thing? 

Rsync?  I've used it for file backups.  Can it handle the rest of it?

RAID 1?  Worth it?

---

### Post by egeezer on 2015-11-26
Sounds like you will simply be doing a dual-drive, dual boot of the same system, so you would have to do parallel updates to keep in sync.  Otherwise, I would think your original system would see the new one as just another mountable.

---

### Post by tgalati4 on 2015-11-27
Why couldn't you set up a RAID1 (simple mirror) using *mdadm* and remove one of the drives and boot to test it.  If it boots, then you are happy; put the drive back.  A week later, remove the other drive and see if it boots.  If it so, you are happy; put the drive back.

Repeat this procedure once a quarter or once a year to verify that you have two bootable images.

The problem with having two different drives synchronized is that you will have UUID issues with GRUB and the boot process.  With a single RAID1 array, you always have the current snapshot.  When you return the drive, then *mdadm* should reimage the drive to make sure you have identical snapshots.  How long this takes, I do not know.  I don't know if *mdadm* wipes the drive completely and reimages the entire drive as a mirror (which takes a lot of time and some data risk) or if it simply compares the inodes and modifies them so they are similar--just adding the differences to make them mirrored.

I don't know how btrfs makes a difference, since the RAID1 pool is an abstraction above the file system level.  I would use ext4 first, since it has been around longer and is perhaps more stable.

---

