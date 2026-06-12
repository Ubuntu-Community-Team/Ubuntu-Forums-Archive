---
title: "Multiple issues in trying to recover data from damaged partition"
date: 2018-09-14
forum: General Help
---

### Post by Shikhar_Raje on 2018-09-14
Hi All,

I've described my problem and the steps that I've tried to take here: [https://askubuntu.com/questions/1075393/problems-with-recovering-data-using-ecryptfs-from-live-disk](https://askubuntu.com/questions/1075393/problems-with-recovering-data-using-ecryptfs-from-live-disk) . I'm reposting it here in case someone might be able to help.

Please help me! As I've mentioned on the post, I have some very personal files that I really cannot afford to lose. I've spent a lot of time on these forums and I've tried a lot of things, but nothing seems to be working, and I'm at the end of my rope!

---

### Post by TheFu on 2018-09-14
encryptfs isn't used with boot-time Linux encryption.  That would be dm-crypt. Is it also likely using LVM, since that is the default for whole drive encryption.

I think I've outlined the steps in these forums a few times previously.  Look for **vgchange** and **cryptsetup** - you'll need those tools.  But I'm assuming you didn't do something funky, non-standard. You'll need to manually decrypt the storage, then manually activate the LVs, then manually mount the LVs you wish to use.   LVM has requirements about LV and VG name collisions, so if the system you are using and the old disk have the same VG/LV names, that won't work.  You'll need to rename them.  
Not exactly what you need, but close: 
* [https://ubuntuforums.org/showthread.php?t=2266650&highlight=cryptsetup+vgchange](https://ubuntuforums.org/showthread.php?t=2266650&highlight=cryptsetup+vgchange)
* [https://ubuntuforums.org/showthread.php?t=2306680&highlight=cryptsetup+vgchange](https://ubuntuforums.org/showthread.php?t=2306680&highlight=cryptsetup+vgchange)
* [https://ubuntuforums.org/showthread.php?t=2392561&highlight=cryptsetup+vgchange](https://ubuntuforums.org/showthread.php?t=2392561&highlight=cryptsetup+vgchange) my notes about LUKS and LVM.
You don't need to do the chroot, grub or initramfs stuff.

Some other handy commands, lvs, pvs, vgs, lsblk  These each show compressed information than the lvdisplay, vgdisplay and pvdisplay tools which show details that aren't usually needed.

Whenever using encryption, great backups are mandatory, 100% of the time.  There isn't any solution should either the storage medium fail or there be some logical issue. Backups are the only solution.  Please learn this before it is too late, assuming it isn't already.

---

### Post by oldfred on 2018-09-14
I know nothing about LVM nor encryption.

These threads seem to have more details.
       Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995)
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

