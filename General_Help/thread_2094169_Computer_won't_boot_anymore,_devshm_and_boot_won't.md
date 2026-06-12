---
title: "Computer won't boot anymore, /dev/shm and /boot won't mount"
date: 2012-12-13
forum: General Help
---

### Post by Stonecold1995 on 2012-12-13
My computer's no longer booting.  I rebooted because of a kernel update after 12 days of uptime, and for seemingly no reason I now get this error:

[[IMG]http://www.pictureshack.us/thumbs/82934_IMG_20121212_225340_434.jpg[/IMG]](http://www.pictureshack.us/images/82934_IMG_20121212_225340_434.jpg)

I usually get an error saying /dev/shm is already mounted, but it continues booting, but now nothing is booting!  It just hangs as you see in the screenshot.

I am not able to choose any options when it says:
```
keys:Press S to skip mounting or M for manual recovery
```
about /boot because it immediately shows the password prompt for my second disk.

**EDIT: If I rapidly press "S" after entering my first password but before my second one apparently skips mounting /boot and my computer is able to boot, but the boot partition (/dev/sdb1) has to be mounted manually if I want to access files in /boot.  And when I boot up apparently my computer will try creating /boot (because it isn't mounted it thinks it doesn't exist) and puts the directory "grub" in there.**

Why isn't /boot mounting correctly at startup anymore?

---

### Post by duke.tim on 2012-12-13
This is what the man page states about system error 2. Maybe someone out there will know what to do with this.

> 2

system error (out of memory, cannot fork, no more loop devices)

---

### Post by SeijiSensei on 2012-12-13
Have you run fsck against the partition where boot is located?  Do that in recovery mode or after booting from a CD/USB drive.

---

### Post by Stonecold1995 on 2012-12-13
> **SeijiSensei said:**
> Have you run fsck against the partition where boot is located?  Do that in recovery mode or after booting from a CD/USB drive.
Yes, and /boot is not corrupt.  From what I can tell, it mounts very early on in the boot process (which is why GRUB works and the kernel can start its thing), but as soon as the computer begins to mount / and /home (and /tmp, etc), /boot is unable to mount, so I have to rapidly press "S" to skip mounting it.

---

### Post by Rexilion on 2012-12-14
I see that it trips over (possible stale) entry's in /etc/mtab.

Try removing the references to the troubled mountpoints located in /etc/mtab and try again.

---

### Post by Stonecold1995 on 2012-12-14
> **Rexilion said:**
> I see that it trips over (possible stale) entry's in /etc/mtab.

Try removing the references to the troubled mountpoints located in /etc/mtab and try again.
```
/dev/mapper/sdb5_crypt / ext4 rw,noatime,discard,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /tmp tmpfs rw,mode=1777 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
tmpfs /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
/dev/mapper/sda1_crypt /home ext4 rw,noatime,errors=remount-ro 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sdb1 /boot ext2 rw 0 0
```

Is there anything wrong with my /etc/mtab?

---

### Post by Rexilion on 2012-12-14
Your mtab mensions '/dev/sdb1 /boot'. Is it really mounted? If not, than that could be a problem. However, I think that it's not the root cause...

Can you provide the output of:

'sudo dmesg' and paste it on pastebin.com? Boot sequence mentions FS issue's...

---

### Post by Stonecold1995 on 2012-12-14
> **Rexilion said:**
> Your mtab mensions '/dev/sdb1 /boot'. Is it really mounted? If not, than that could be a problem. However, I think that it's not the root cause...
It says it's mounted in /etc/mtab but it doesn't mount.  I have to mount it manually after my computer starts.

> **Rexilion said:**
> Can you provide the output of:

'sudo dmesg' and paste it on pastebin.com? Boot sequence mentions FS issue's...

[http://pastebin.com/JWxPya4V]("http://pastebin.com/JWxPya4V")

---

### Post by Rexilion on 2012-12-14
Could you reboot and paste dmesg again?

I see almost solely messages like these:

'[30410.746082] CPU4: Package power limit normal'

Do you overclock or something??

---

### Post by Stonecold1995 on 2012-12-14
> **Rexilion said:**
> Could you reboot and paste dmesg again?

I see almost solely messages like these:

'[30410.746082] CPU4: Package power limit normal'

Do you overclock or something??

[http://pastebin.com/0vEby1wy](http://pastebin.com/0vEby1wy)

No, I don't overclock.  I run Folding@home 24/7 so my CPU usage stays at around 90%.  I'm using a laptop but it's a high-end gaming laptop so it has very good ventilation.

---

### Post by Rexilion on 2012-12-15
Can you provide the output of:

```
uname -a
cat /proc/filesystems
```

Do you build your own kernel? Did you modify it? Or install a kernel from a non-standard location?

---

### Post by Stonecold1995 on 2012-12-15
> **Rexilion said:**
> Can you provide the output of:

```
uname -a
cat /proc/filesystems
```
```
alex@kubuntu:~$ uname -a
Linux kubuntu 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:51:59 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
alex@kubuntu:~$ cat /proc/filesystems
nodev   sysfs
nodev   rootfs
nodev   bdev
nodev   proc
nodev   cgroup
nodev   cpuset
nodev   tmpfs
nodev   devtmpfs
nodev   debugfs
nodev   securityfs
nodev   sockfs
nodev   pipefs
nodev   anon_inodefs
nodev   devpts
        ext3
        ext4
nodev   ramfs
nodev   hugetlbfs
        vfat
nodev   ecryptfs
        fuseblk
nodev   fuse
nodev   fusectl
nodev   pstore
nodev   mqueue
        btrfs
        ext2
nodev   binfmt_misc
```

> **Rexilion said:**
> Do you build your own kernel? Did you modify it? Or install a kernel from a non-standard location?

No, I'm using the generic kernel from the repositories.  I have compiled my own kernel before with the GrSecurity patch before (many weeks before this problem started happening), but the Nvidia driver didn't work so I'm not using that kernel currently, only the default for Ubuntu.

---

### Post by Rexilion on 2012-12-16
Long shot, but try this:

Open /etc/mtab and remove all references to /boot and /dev/shm. Then reboot, the problem should be gone.

---

### Post by Stonecold1995 on 2012-12-19
I removed the "discard" option from the entry for /boot in /etc/fstab (I think ext2 doesn't support discard) and it's working now.

---

