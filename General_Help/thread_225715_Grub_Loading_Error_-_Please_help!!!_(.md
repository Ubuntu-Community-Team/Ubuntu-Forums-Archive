---
title: "Grub Loading Error - Please help!!! :("
date: 2006-07-30
forum: General Help
---

### Post by pat270881 on 2006-07-30
hello,

I created a backup with cpio like find /home | cpio -ov /dev/hda3. I created the backup on my root drive (hda3). After that I wasnt able any more to start the file browser and was not able to look in the terminal for the root directories. So I started ubuntu once more and when the reboot comes to Loading the Grub menu there occurs:

Please wait, while loading...
Error 17.

Does anybody know what that mean? I am a very desperate.:( I also have windows on my laptop and there are important data on it, but I am also not able to start windows because the grub menu does not load.

hopefully someone could help me here?? :confused:

---

### Post by pat270881 on 2006-07-30
Hi,

I booted the laptop with the ubuntu desktop cd and when I use the fdisk command in the terminal I got this output

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2060    16546918+   7  HPFS/NTFS
/dev/hda2            3443        4863    11414182+   f  W95 Ext'd (LBA)
/dev/hda3            2061        3442    11100915   83  Linux
/dev/hda5            3507        4863    10900071    7  HPFS/NTFS
/dev/hda6            3443        3475      265041   82  Linux swap / Solaris
/dev/hda7            3476        3506      248976   83  Linux

Actually the hda3 is my root partition. So I tried to mount this partition because I have very important data on that partition which I need urgently :sad: 

So I created a directory under mnt - test and tried to mount the partition

ubuntu@ubuntu:/$ sudo mount -t ext2 /dev/hda3 /mnt/test
mount: wrong fs type, bad option, bad superblock on /dev/hda3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

But as you see it didnt work.

the dmesg
ubuntu@ubuntu:/$  dmesg | tail
[4294976.864000] Bluetooth: L2CAP ver 2.8
[4294976.864000] Bluetooth: L2CAP socket layer initialized
[4294977.603000] Bluetooth: RFCOMM socket layer initialized
[4294977.603000] Bluetooth: RFCOMM TTY layer initialized
[4294977.603000] Bluetooth: RFCOMM ver 1.7
[4295466.951000] SQUASHFS error: Can't find a SQUASHFS superblock on hda3
[4295481.989000] VFS: Can't find ext3 filesystem on dev hda3.
[4295503.108000] SQUASHFS error: Can't find a SQUASHFS superblock on hda3
[4295592.491000] SQUASHFS error: Can't find a SQUASHFS superblock on hda3
[4295637.631000] VFS: Can't find an ext2 filesystem on dev hda3.

Please can someone help me in order to access the data on that partition...??:confused:

---

