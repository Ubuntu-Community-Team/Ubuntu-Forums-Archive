---
title: "Recovery maintenance mode Ubuntu 22.04"
date: 2024-04-17
forum: General Help
---

### Post by dalpets on 2024-04-17
For the purpose of  resetting my forgotten authentication I have attempted to use recovery mode to drop me to the root shell but it does not do so. It only leaves me with a root prompt for maintenance.
Advanced options appear for both 6.5.0-26/27 but neither provide the root shell GUI. I have also looked at UEFI mode within recovery but my bias shows no reference to UEFI.

Motherboard Gigabyte H412M S2H
Graphics Nvidia GT1030

Help please. 
Thanks.

---

### Post by TheFu on 2024-04-17
Uh .. root doesn't have any GUI.  You get a shell to perform stuff.
If you just want to reset a password, from that shell, use

```
# passwd dalpets 
```
Which will set a new password for the username, dalpets.  This assumes that all the storage is mounted for the OS in the correct place.  I haven't done this in some time, so I don't know if that actually happens.

If it doesn't mount the OS storage, then you'll need to mount it in a specific way and make a chroot environment to use the correct tools, have the correct libraries available and update the correct user passwd, group, and shadow files inside /etc/ .  Obviously, if using LDAP or some other external authentication, this isn't the way to reset a password, but hardly any home users of Linux setup LDAP or other authentication like NIS, NIS+ or an x.500 directory service. ;)  I assume you didn't.

It is also handy to run **fsck** on Native Linux file systems (not NTFS/exFAT, FAT32... ), but native Linux file systems.  Also, fsck for zfs or btrfs need to use the tools specific to those file systems.

---

