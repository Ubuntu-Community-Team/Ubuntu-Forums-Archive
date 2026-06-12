---
title: "Can't boot up :-("
date: 2006-11-05
forum: General Help
---

### Post by somersetsimon on 2006-11-05
I've been running Dapper for a week or so and even got my wireless network and network printer working.

This morning, all my ubuntu applications stopped working. I couldn't even bring up a terminal window to sort the problem out. I remembered that Ctrl-Alt-F2 did something, so I pressed those keys. It then jumped out of X windows, back to something that looked like recovery mode with a login prompt. I then rebooted, but the boot failed with the following messages, then hung:

Mounting root filesystem

[HTML]mount: Mounting /dev/hdd1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such drive or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init[/HTML]

I have two hard disks with XP on one and Ubuntu on the other.

What happened and how do I recover from it?

---

### Post by somersetsimon on 2006-11-05
> **somersetsimon said:**
> I've been running Dapper for a week or so and even got my wireless network and network printer working.

This morning, all my ubuntu applications stopped working. I couldn't even bring up a terminal window to sort the problem out. I remembered that Ctrl-Alt-F2 did something, so I pressed those keys. It then jumped out of X windows, back to something that looked like recovery mode with a login prompt. I then rebooted, but the boot failed with the following messages, then hung:

Mounting root filesystem

[HTML]mount: Mounting /dev/hdd1 on /root failed: Invalid argument
mount: Mounting /root/dev on /dev/.static/dev failed: No such drive or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/init[/HTML]

I have two hard disks with XP on one and Ubuntu on the other.

What happened and how do I recover from it?

BTW, I saw a thread that seemed similar that asked for this information after booting with the live CD:

[HTML]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdd: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4905    39399381   83  Linux
/dev/hdd2            4906        4998      747022+   5  Extended
/dev/hdd5            4906        4998      746991   82  Linux swap / Solaris
ubuntu@ubuntu:~$[/HTML]

---

### Post by somersetsimon on 2006-11-06
Bump.
If it's any help, I dual boot with XP. GRUB and XP still seem to be working fine.

Simon

---

### Post by somersetsimon on 2006-11-06
Has anyone got any suggestions or links to useful threads or should I just reinstall (again :-( )

---

### Post by somersetsimon on 2006-11-06
> **somersetsimon said:**
> BTW, I saw a thread that seemed similar that asked for this information after booting with the live CD:

[HTML]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2433    19543041    7  HPFS/NTFS

Disk /dev/hdd: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        4905    39399381   83  Linux
/dev/hdd2            4906        4998      747022+   5  Extended
/dev/hdd5            4906        4998      746991   82  Linux swap / Solaris
ubuntu@ubuntu:~$[/HTML]

I found a few other posts with similar problems and they suggested running the following commands from the Live CD:

sudo mount /dev/hdd1/mnt

This gives the response:

mount: can't find /dev/hdd1/mnt in /etc/fstab or /etc/mtab

I had a look at /etc/fstab from the Live CD and it was empty

Anything else I could try?

---

### Post by somersetsimon on 2006-11-07
OK, last bump before I reinstall. I wonder if Edgy would be less likely to cause this problem? I've had once with Kubuntu Dapper and once with Ubuntu Dapper.

---

