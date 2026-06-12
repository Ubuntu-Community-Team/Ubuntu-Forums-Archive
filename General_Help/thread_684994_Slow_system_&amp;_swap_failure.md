---
title: "Slow system &amp; swap failure"
date: 2008-02-01
forum: General Help
---

### Post by Baasha on 2008-02-01
I have noticed that when I have my browser and OpenOffice running at the same time the browser takes a long time to load pages that have several Jpgs on them.  I also paid attention to the boot up screen, and although the messages scroll past pretty fast, I noticed that when it said something about my swap partition it said fail instead of OK.

So I ran an fdisk command and a swapon command in the terminal and this is what I got:

Code:
bob@ubuntu:~$ sudo fdisk -l
[sudo] password for bob:

Disk /dev/hda: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x703e7a4e

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         914     7341673+   7  HPFS/NTFS
/dev/hda2             915        7475    52701232+   7  HPFS/NTFS

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00091d63

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         973     7815591   83  Linux
/dev/sda2             974       24321   187542810    5  Extended
/dev/sda5           24134       24321     1510078+  82  Linux swap / Solaris
/dev/sda6           23161       24133     7815591    b  W95 FAT32
/dev/sda7             974       23159   178208982   83  Linux

Partition table entries are not in disk order
bob@ubuntu:~$ swapon -s
Filename                                Type            Size    Used    Priority
bob@ubuntu:~$ 


The first thing I noticed is that sda2 and sda5 (my swap) seem to be overlapped, but I don't know if this is the way it is supposed to be or not.  And the second thing is that the swapon command doesn't return anything.  Does that mean my swap partition is no longer being recognized?

In any event, I need some help to fix this.  Does anyone recognize what is wrong, and can you tell me what to do about it?

Thanks in advance.

---

### Post by taurus on 2008-02-01
Can you post the outputs of these commands from a terminal?

```
free
cat /etc/fstab
```

---

### Post by Baasha on 2008-02-01
Here is what I got:
bob@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:        516124     507556       8568          0      22336     241244
-/+ buffers/cache:     243976     272148
Swap:            0          0          0
bob@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=d1506f7b-b5d3-4eec-bef0-226f8233f27f / ext3 defaults,errors=remount-ro 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=92c2f737-7431-443f-a562-75acd28cbef3 /home ext3 defaults 0 2
# /dev/sda6 -- converted during upgrade to edgy
UUID=ED73-79D2 /media/sda6 vfat iocharset=utf8,umask=000 0 0
# /dev/sda5 -- converted during upgrade to edgy
UUID=76d65bb7-5069-4594-b604-6133f89213f4 none swap sw 0 0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cdrom        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=0AB86390B86378D9 /windows1 ntfs nls=utf8,umask=0222 0 0
# /dev/hda2 -- converted during upgrade to edgy
UUID=F6F49983F4994731 /windows2 ntfs nls=utf8,umask=0222 0 0
bob@ubuntu:~$

---

### Post by taurus on 2008-02-01
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and place a # in front of this line to comment it out.

```
**[COLOR="Blue"]#[/COLOR]**UUID=76d65bb7-5069-4594-b604-6133f89213f4 none swap sw 0 0
```
Then on the next line, new line, add

```
/dev/sda5   none   swap   sw   0   0
```
Save it and then run

```
sudo mount -a
free
```

---

### Post by Baasha on 2008-02-02
Thanks Taurus, that seemed to have fixed it, and that's no bull :lolflag:

---

