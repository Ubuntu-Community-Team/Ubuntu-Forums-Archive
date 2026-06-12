---
title: "[SOLVED] wubi crash on linux-side install"
date: 2008-07-08
forum: General Help
---

### Post by PhaedrusDE on 2008-07-08
Total Linux beginner here

I installed wubi 8.04.1 yesterday on my laptop after a fresh windows install.  The download goes fine and the windows-side installation goes off without a hitch.  On the Ubuntu loadup I get the ubuntu screen for a second then it crashes to a screen that says

```

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

This looks nothing like what the install looked like when I wubi'ed my desktop.

Also, I'm unable to uninstall wubi to try again, however, this might be related to [this ]("http://ubuntuforums.org/showthread.php?t=851337")error.  If nothing else I'll try that uninstaller to burn it down and try again, but I figured in any case this might be an error worth raising.

---

### Post by ago on 2008-07-08
Do you use raid/encrypted disks by any chance?

What is the output of the following commands?

cat /proc/cmdline
cat /proc/mounts
cat /proc/partitions
grep -i err /casper.log
grep -i mount /casper.log

To uninstall you can use: [http://ubuntuforums.org/showpost.php?p=5340574&postcount=15](http://ubuntuforums.org/showpost.php?p=5340574&postcount=15)

---

### Post by PhaedrusDE on 2008-07-08
No encrypted disks, and this laptop had wubi 8.04 installed on it before I had to reformat due to windows-based problems.

results

cat /proc/cmdline
```
root=UUID=SOEE-F381 loop=/ubuntu/disks/root.dsk ro quiet splash
```

cat /proc/mounts
```
rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw, relatime 0 0
fusectl /sys/fs/fuse/connections fusectl rw,relatime 0 0
/dev/disk/by-uuid/DOEE-F381 /host vfat rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1 0 0
```

cat /proc/partitions
```
major minor  #blocks  name

   8     0   97885784 sda
   8     1    4088511 sda1
   8     2   46540305 sda2
   8     3   47054385 sda3
```

grep -i err /casper.log
```
grep: /casper.log: No such file or directory
```

grep -i mount /casper.log
```
grep: /casper.log: No such file or directory
```

---

### Post by ago on 2008-07-08
You might want to run chkdsk
Press esc at boot after ubuntu and select recovery mode, see if you can get more errors

---

### Post by PhaedrusDE on 2008-07-08
In recovery mode

From where the problems seem to start:

```

/host/ubunutu/disks/root.disk: unknown volume type
[   22.512380] loop: module loaded
mount: Mounting dev/loop0 on /root failed: No such device
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: running /scripts/init-bottom ...
mount: Mounting /root/dev on dev/.static/dev failed: No such file or dierctory
Done.
mount: Mounting /sys on root/sys failed: No such file or dierctory
mount: Mounting proc on root/proc failed: No such file or dierctory
Target filesystem doesn't have sbin/init

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

Don't know how to scroll up to see if any errors popped up earlier.

---

### Post by ago on 2008-07-08
You can scroll with shift+pgup

What is the output of

ls -al /host/ubuntu/disks   #that is LS -AL in lower case
touch /host/writetest
losetup -a
losetup /host/ubuntu/disks/root.disk /dev/loop3
mount /dev/loop3 /root
mount -o loop /host/ubuntu/disks/root.disk /root

---

### Post by PhaedrusDE on 2008-07-08
ls -al /host/ubuntu/disks
```
-rwxr-xr-x   1 0        0       4000000000 usr.disk
-rwxr-xr-x   1 0        0       1000000000 swap.disk
-rwxr-xr-x   1 0        0       1000000000 home.disk
-rwxr-xr-x   1 0        0       4000000000 root.disk
drwxr-xr-x   2 0        0            32768 shared
drwxr-xr-x   3 0        0            32768 boot
drwxr-xr-x   6 0        0            32768 ..
drwxr-xr-x   4 0        0            32768 .
```

touch /host/writetest
nothing

losetup -a
nothing

losetup /host/ubuntu/disks/root.disk /dev/loop3
```
ioctl: LOOP_SET_ID: Inappropriate ioctl for device
```

mount /dev/loop3 /root
```
[   22.820771] bio too big device loop3 (1 > 0)
[   22.820831] FAT:unable to read boot sector
mount: Mounting /dev/loop3 on /root failed: Input/output error
```

mount -o loop /host/ubuntu/disks/root.disk /root
```
mount: Mounting /dev/loop0 on /root failed: Invalid argument
```

---

### Post by ago on 2008-07-08
losetup /dev/loop3 /host/ubuntu/disks/root.disk
mount /dev/loop3 /root
ls /root

---

### Post by PhaedrusDE on 2008-07-08
losetup /dev/loop3 /host/ubuntu/disks/root.disk
nothing

mount /dev/loop3 /root
```
mount: Mounting /dev/loop3 on /root failed: Invalid argument
```

ls /root
nothing

---

### Post by PhaedrusDE on 2008-07-08
OK, just logged in to my laptop and realized something that might be causing the problem - My windows install only reformatted the C: partition, and the old wubi install was on the D: partition.  But when I reinstalled (to the D:/, which in hindsight I probably should have checked >.<), it didn't ask to uninstall the old wubi (as I assume it should) probably because I ran the installer from the desktop (which is on C:/).  I'm assuming this situation (double install) would wreak some havok. 

Hopefully the uninstall will clear the garbage out so I can try again.  I'll wait around a few minutes in case you want me to run some more tests though, ago.

---

### Post by PhaedrusDE on 2008-07-08
Uninstalled using the above file and reinstalled on C:/ - worked like a charm.

---

