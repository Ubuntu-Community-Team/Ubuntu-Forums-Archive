---
title: "Can not mount ntfs storage drive"
date: 2018-05-13
forum: General Help
---

### Post by hrsetrdr on 2018-05-13
I just installed Ubuntu 16.04 on a desktop that I (for reasons that escape me) had recently installed Windows 10.   Previously on this desktop I had only Linux, and could mount the ntfs drive fine, as long as I had the ntfs-3g driver installed.

I believe that having Windows 10 has caused some metatdata to be added to the ntfs drive, here's the error message when trying to mount the ntfs drive:

```
Error mounting /dev/sdb1 at /media/user/datastore: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000" "/dev/sdb1" "/media/user/datastore"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sdb1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

Not sure how to fix this, any help would be much appreciated.

---

### Post by dino99 on 2018-05-13
uuid has probably changed. Does that happen when you manually try to mount that ntfs partition ? Check blkid and fstab

---

### Post by ajgreeny on 2018-05-13
If you have a default installation of Windows 10, your ntfs partition will have been mounted when running Windows, and as far as Ubuntu is concerned, is probably still in use, as Windows does not fully shutdown and unmount drives or partitions unless you have disabled fast-startup, not fast boot in the BIOS, but fast-startup which is a Windows setting.

Have a look through the Windows settings which I can not help you with as I no longer run Windows and if necessary disable fast-startup.

---

### Post by hrsetrdr on 2018-05-13
> **ajgreeny said:**
> If you have a default installation of Windows 10, your ntfs partition will have been mounted when running Windows, and as far as Ubuntu is concerned, is probably still in use, as [COLOR="#FF0000"]Windows does not fully shutdown and unmount drives [/COLOR]or partitions unless you have disabled fast-startup, not fast boot in the BIOS, but fast-startup which is a Windows setting.

Have a look through the Windows settings which I can not help you with as I no longer run Windows and if necessary disable fast-startup.

Windows not fully shutting down and unmounting the drive was the issue.  Weird.  Anyway, I used the Windows "Power Shell" and gave it a shutdown -s command. Upon booting back into Ubuntu- bingo, have access.  

 I didn't actually think that would work, as in my mind, the machine was OFF, then turned back on when I originally ran into the mounted drive issue, so how could any OS still have a dirve mounted.

"[solved]"      Thanks for your replies.

---

### Post by yancek on 2018-05-13
Using the restart option is better because it actually shuts down, strange as it may seem.  Explained in detail at the link below.  There are a number of other ways to do it including from the windows powershell which you seem to have found.  ONe purpose of this is to make it appear windows is booting faster than it actually would from a shutdown/restart so this is the fastboot/hibernation option windows uses.  Some updates will turn fastboot/hibernation back on in windows so you need to keep an eye out for that in the future.  If you see this problem again, this is very likely going to be the reason.

 [https://www.howtogeek.com/349114/shutting-down-doesnt-fully-shut-down-windows-10-but-restarting-it-does/](https://www.howtogeek.com/349114/shutting-down-doesnt-fully-shut-down-windows-10-but-restarting-it-does/)

---

### Post by hrsetrdr on 2018-05-14
> **yancek said:**
> Using the restart option is better because it actually shuts down, strange as it may seem.  Explained in detail at the link below.  There are a number of other ways to do it including from the windows powershell which you seem to have found.  ONe purpose of this is to make it appear windows is booting faster than it actually would from a shutdown/restart so this is the fastboot/hibernation option windows uses.  Some updates will turn fastboot/hibernation back on in windows so you need to keep an eye out for that in the future.  If you see this problem again, this is very likely going to be the reason.

 [https://www.howtogeek.com/349114/shutting-down-doesnt-fully-shut-down-windows-10-but-restarting-it-does/](https://www.howtogeek.com/349114/shutting-down-doesnt-fully-shut-down-windows-10-but-restarting-it-does/)

Thanks, that is an interesting strategy, I've not used Win 10 much, not trying to be a "Windows basher" but I've found more potential for frustration in using W10 than I've found usefulness.   

I actually installed Fedora 28 over the W10 install, so there won't be any more strange issues with accessing the storage drive.

---

