---
title: "Cant access hard drive"
date: 2016-10-17
forum: General Help
---

### Post by snowcap96 on 2016-10-17
Hi,

Recently installed Ubuntu from Windows 10. Wanted to run Ubuntu alongside Windows and keep all my files from windows while using Ubuntu. Everytime i try to access my files it comes up with,

 Unable to access “Hard Drive 1TB”
Error mounting /dev/sdb1 at /media/tom/Hard Drive 1TB: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/tom/Hard Drive 1TB"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

Can anyone help me out so I can access my windows files while on Ubuntu? I'm new to linux so not sure how to go about it. 

Cheers


EDIT: 

FIX: You need to go back to the Windows OS and turn off hibernation in Shutdown settings. Problem solved for me :)

---

### Post by oldrocker99 on 2016-10-17
Open a terminal from within Windows and issue the command FIXBOOT. That **might** fix your drive, which does show an error. You shouldn't have any problem at all accessing a healthy NTFS drive; I do it with every reboot.

---

### Post by ajgreeny on 2016-10-17
> Recently installed Ubuntu from Windows 10. Wanted to run Ubuntu alongside Windows and keep all my files from windows while using Ubuntu.
If you installed Win10 yourself using BIOS not UEFI, does this mean what I think it might mean, ie,  that from a running Windows OS you installed Ubuntu using the old, and now deprecated **wubi**?

If so, I suspect you will not get much help here as most users have not seen nor used wubi for a very long time, and if this is your situation, I suggest you investigate a proper dual boot system

See [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot) for more detailed info

---

### Post by ajgreeny on 2016-10-18
Tell us please what the solution was; it is very helpful for users searching the forum.

---

