---
title: "Mount 'Hibernated' partition."
date: 2014-03-01
forum: General Help
---

### Post by Tyler_Dence on 2014-03-01
Hey all, I just purchased a new laptop, and it came with windows 8 on it.

Out of the 1 TB drive, I partitioned it so that I have the windows partitions (that came with the computer), two ubuntu partitions, and one 200GB NTFS "common" partition, for files that all the operating systems can access. The issue is that when I boot and subsequently shut down from windows, the common partition is unable to be mounted in read/write mode. Is there any way to stop windows from "locking", if you will, the "common" drive?

Here's my etc/fstab
```
# /etc/fstab: static file system information.#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=7964d7e5-56aa-4969-8728-59ceb068afaf /               ext4    errors=remount-ro 0       1
/dev/sda10	/media/common	ntfs	user,exec	0	2
```

It fails to mount on boot, and when I try to manually mount it, it fails as well:
```
# mount /dev/sda10 /media/commonThe disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda10': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```

---

### Post by oldfred on 2014-03-01
I do not know if there is a way to separately unmount a second partition in Windows like you do in Linux.

You probably just need to make sure fast boot or the always on hibernation if off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by Tyler_Dence on 2014-03-01
> **oldfred said:**
> I do not know if there is a way to separately unmount a second partition in Windows like you do in Linux.

You probably just need to make sure fast boot or the always on hibernation if off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

I would have thought that there was a way to prevent this one drive from being touched without disabling fast boot, but it appears that it isn't possible.

Thanks for those links, though. The first thread helped explain some stuff.

---

