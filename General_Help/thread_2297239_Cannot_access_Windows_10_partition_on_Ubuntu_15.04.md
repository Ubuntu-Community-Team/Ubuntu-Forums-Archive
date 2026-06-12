---
title: "Cannot access Windows 10 partition on Ubuntu 15.04"
date: 2015-10-02
forum: General Help
---

### Post by Henry_Fisher on 2015-10-02
Anytime I try mounting my Windows 10 Partition on Ubuntu 15.04, I get the following message: 

Error mounting /dev/sda4 at /media/henfish/72720B3A720B0299: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sda4" "/media/henfish/72720B3A720B0299"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

[ATTACH=CONFIG]264777[/ATTACH]

I fully understand what this means and the course of actions which should be taken to resolve it, but sadly nothing has worked. I have done the following:
-Disabled Fast startup in Windows
- Disabled Hibernation mode
- Done a complete shut down Holding the shift key when turning off the computer to go into the troubleshooting menu and shutting down from there.


Nothing has worked and I believe that maybe Windows 10 introduced some type of encryption or no more access somehow? 

Any help is much appreciated and I thank you in advance. If any more information is needed I am happy to provide it.

---

