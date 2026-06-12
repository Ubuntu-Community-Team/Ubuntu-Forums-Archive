---
title: "Permission on external hard drives"
date: 2016-04-03
forum: General Help
---

### Post by jwn-2 on 2016-04-03
Ubuntu 14.04 LTS

I have two external hard drives. Both are NTFS and in all aspects exactly the same, except that one is a 100 GB disk and the other one a 2TB disk. On the smaller disk files are deleted directly, while on the larger one it goes to the rubbish bin. Also on the smaller one I can run scripts that I create or store on that disk even though the owner is root (all text files are by default executable), but on the larger one all text files are by default not executable, and I am unable to change it to executable, even though I am the owner of the file. Why the difference and where can I change these preferences?

---

### Post by TheFu on 2016-04-03
Control of permissions for non-Linux file systems is control through the mount options.  So - how do you mount each of these different devices?  Make them identical.

Mostly, if you use a GUI to mount, then you don't have the control over permissions.  Manually modify the /etc/fstab file for the disks to have complete control. There is a help page for that online - "ubuntu fstab ntfs" will find it.

---

### Post by jwn-2 on 2016-04-04
Thank you TheFu, that helped.

I am however still a bit confused though as to what options to use to gain full control over both disks, so that I can change the permissions for each file individually? I have tried several combinations of options, but the disk comes out either as root as the owner and I can't change anything, or me as the owner (with different permissions) and I still can't change anything. Help would be appreciated.

---

### Post by TheFu on 2016-04-04
The easy answer is to use a Linux file system for that requirement.

The harder answer is to setup a userid mapping file so that Linux knows how the Windows-to-Linux userid mapping happens and then use the permissions option for the mount, inside the /etc/fstab. I think there is a tool to help create this file - usermap. [http://manpages.ubuntu.com/manpages/trusty/man8/ntfs-3g.usermap.8.html](http://manpages.ubuntu.com/manpages/trusty/man8/ntfs-3g.usermap.8.html)

FAT, FAT32, vFAT do not support permissions - at all.

Good luck.

---

### Post by jwn-2 on 2016-04-05
Thanks TheFu. I can at least mount all my disks now so that I have permission to execute and to change files. It is not ideal but it is acceptable. BUT I do have a new problem now: If any of the disks are not present at boot time, the system does not boot automatically. I have to press "S" (skip) for each disk not present before the system finish booting. Adding the "nofail" option also seems to make no difference here. I have even tried running a script at boot that mounts the disks, and then I am able to boot without user interchange, BUT then if I remove the disk and remount it later again, the permissions are different. With a line in etc/fstab the permissions at least stay the same. Is there any way that I can make the system boot up automatically without having to tell it to skip non-present disks?

---

### Post by TheFu on 2016-04-05
Temporary disks like this are a hassle.  I use autofs to make them mount only on-demand. The trick is to have control over when the demand happens - so it only happens when the disk ARE there.  Until the disk is accessed, it isn't mounted. When it it unused for a few minutes, autofs removes the mount automatically. Of course, if you unplug the disk and take it away, it **must** be un-mounted first.  You can manually umount it with sudo if needed too.

Autofs mounts work like fstab mounts, so they show up as local disks everywhere, just like you want.  

I've never used autofs for NTFS drives, but it should work.  Currently using it for NFS, remote Win-shares, and for USB disks with Linux file systems. The remote windows-shares don't always work, but a reboot on the Windows side fixes it.  The first time you set this up, it isn't clear, but soon it becomes 2nd nature and takes 20 seconds. [https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs) is the help for this.  I've been using it for 20+ yrs, so never read that pg.

If you get stuck, post the fstab that is working and someone should be able to translate that into the auto.master and auto.ntfs file settings pretty easily.

Honestly, if you can, it is much easier to ... 
a) make the storage Linux file system - ext4
b) make this device non-portable and
c) just leave it connected and powered on.  
If a Windows machine needs access, use samba.
For remote access setup ssh/sftp with keys and then the data is available from anywhere in the world.

If this is a backup disk, I'd add mount/umount to the backup script. Be certain to validate that the mount worked. Sucks when a backup keeps running, but the necessary storage isn't there. I speak from experience. A full / is bad.  I've helped a few folks create these USB-backup scripts at my LUG. We started simple, but they ran with the script and made something impressive that could be restored. I was proud. ;)

But it just depends on the use for this drive. You'll do the best thing for your environment.

---

### Post by jwn-2 on 2016-04-11
Thanks for all your advise TheFu. I have decided to reformat my disks for Linux compatability after all. You are right, it makes everyrhing much easier and I can still access the data in Windows.

---

