---
title: "bootup hang on fsck; hdb not mounting?"
date: 2007-01-21
forum: General Help
---

### Post by mrattigan on 2007-01-21
After installing some updates the other day, my system doesn't seem to want to boot.  I believe that my Linux hdd (hdb) is not mounting correctly, as the last text output I get is a bunch of mount usage info, followed by "checking file systems...".  If I boot from a CD, I can mount my partitions and access all my data (I've tried fscking).  

Any thoughts on where to troubleshoot?  I've found a bunch of threads with similar problems, but no solutions that work for me...

**sfdisk -l** yields:
ubuntu@ubuntu:/$ sudo sfdisk -l

Disk /dev/hda: 14593 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hda1   *      0+   2439    2440-  19599268+   7  HPFS/NTFS
/dev/hda2       2440   14592   12153   97618972+   f  W95 Ext'd (LBA)
                start: (c,h,s) expected (1023,254,63) found (1023,0,1)
/dev/hda3          0       -       0          0    0  Empty
/dev/hda4          0       -       0          0    0  Empty
/dev/hda5       2440+  14592   12153-  97618941    b  W95 FAT32
                start: (c,h,s) expected (1023,254,63) found (1023,1,1)

Disk /dev/hdb: 4865 cylinders, 255 heads, 63 sectors/track
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/hdb1          0+   1581    1582-  12707383+  83  Linux
/dev/hdb2       1582    4864    3283   26370697+   f  W95 Ext'd (LBA)
/dev/hdb3          0       -       0          0    0  Empty
/dev/hdb4          0       -       0          0    0  Empty
/dev/hdb5       4800    4864      65     522112+  82  Linux swap / Solaris
/dev/hdb6       1582+   4799    3218-  25848522   83  Linux
ubuntu@ubuntu:/$ 

**fstab** is:
ubuntu@ubuntu:/media/hdb1$ cat etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=0287-7F80  /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb6
UUID=5e9e3496-8171-415a-b323-014345aca1a2 /home           ext3    defaults        0       2
# /dev/hda1
UUID=F0A08C40A08C0F72 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb5
UUID=cf3a5167-0e53-4df3-8716-f64a5bf46c2c none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

relevant **grub/menu.lst**:
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Stemp on 2007-01-21
```
/dev/ /media/floppy0 auto rw,user,noauto 0 0
```

/dev/ ? guess there is a problem here

---

### Post by mrattigan on 2007-01-21
Thanks for the suggestion; unfortunately, that doesn't do it.  If I Ctrl-Alt-Del my way to a prompt, I can manually startx.  However, the /home (which *should* be mounted with /dev/hdb6) is empty.  Is there a way to get more verbose output to see exactly where the wheels are coming off the wagon during boot?

Thanks.

---

### Post by Stemp on 2007-01-21
> If I Ctrl-Alt-Del my way to a prompt

You mean Ctrl+Alt+F1 ? 

> Is there a way to get more verbose output to see exactly where the wheels are coming off the wagon during boot?

dmesg on a command line or view the files /var/log/syslog or  /var/log/messages

> However, the /home (which should be mounted with /dev/hdb6) is empty

for that try the command :

```
sudo mount /dev/hdb6 /home
```

---

### Post by dcstar on 2007-01-21
> **mrattigan said:**
> After installing some updates the other day, my system doesn't seem to want to boot.
......
relevant **grub/menu.lst**:
## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 **ro**
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 **ro** single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

AFAIK the "**ro**" means Read Only, which is probably why your system won't boot.

I would boot off the live CD and edit these out, and then see what happens.

---

### Post by Stemp on 2007-01-21
> AFAIK the "ro" means Read Only, which is probably why your system won't boot.

It's totally normal, usually the line end up with **ro splash quiet**
He just erased the splash boot and the quiet options to look at the errors.

---

