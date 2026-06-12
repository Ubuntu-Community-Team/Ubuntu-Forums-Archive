---
title: "fsck: how long to check 1tb drive?"
date: 2013-01-23
forum: General Help
---

### Post by badperson on 2013-01-23
Hi,
I have a new server build with 4HD's, and during boot fsck was run on one of them saying it hadn't been checked in 235 days. 

The screen says:
```
keys:Press C to cancel all checks in progress
```

It has been going for over an hour and there is no progress indicator...

just want to confirm it's running normally and not waiting on and input from me. 
bp

---

### Post by SeijiSensei on 2013-01-23
It's probably fine.  What filesystem is it?  If you're using the default, ext4, or its immediate predecessor ext3, they use "journaling" to speed up checking. If it is an NTFS file system, I'd look at it from Windows just to be on the safe side.

If you'd prefer to watch it yourself, you can cancel the process and reboot.  Pick the "recovery mode" entry from the GRUB menu at boot.  (If you don't see a menu, hold down the Shift key while booting.)  Pick "root shell" from the menu and, at the "#" prompt, run the command "fsck /dev/XXXX" replacing XXXX with the appropriate partition like /dev/sda1 or /dev/sdb3.  To see more details, run "fsck -v /dev/XXXX" to get "(v)erbose" results.

If this is not the boot drive, you can check it from a terminal without being in recovery mode.  Just make sure to unmount the drive first:

```

cd /
sudo umount /dev/sdc1
sudo fsck -v /dev/sdc1

```

If you cannot umount the drive because you get an "in use" error, you can use the lsof command to find which program(s) are accessing the drive.  If the drive is mounted as, say, /media/videos, then run

```
sudo lsof | grep /media/videos
```

to see what applications are using it, then shut them down and try checking again.

---

