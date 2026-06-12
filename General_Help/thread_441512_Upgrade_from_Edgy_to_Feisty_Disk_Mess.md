---
title: "Upgrade from Edgy to Feisty: Disk Mess"
date: 2007-05-12
forum: General Help
---

### Post by Foucault on 2007-05-12
Hi to all,
I've recently upgraded (through update-manger) my distribution to Feisty. However it seems there was some problem with the drives and as a result system won't boot properly.

First let me inform you on my disk configuration (pre feisty)

**PATA Drive 1**
/dev/hda1 -> NTFS Partition
/dev/hda3 -> FAT32 Partition

**PATA Drive 2**
/dev/hdb1 -> EXT3 Partition mounted on **/**
/dev/hdb2 -> SWAP Partition

**SATA Drive**
/dev/sda1 -> EXT3 Partition mounted on **/home**

Let me inform you that while upgrading I was constantly receiving the following warnings (not sure if the output is exactly as given here, but oh, well..):
```
Generatin initramfs linux-image-<KERNEL NUMBER>
mdadm: /etc/mdadm/mdadm.conf defines no arrays
mdadm: no arrays defined
mdadm: falling back  to emergency procedure initramfs
```

FYI, I don't have any RAID configuration (how could this be done with one sata drive after all).

After rebooting again I left the system boot a little longer. Hitting Ctrl+Alt+F1 gave me the following

```
mdadm: No devices listed in conf file were found
[ata3.0]failed to set xfermode (err_mask=0x40) (about 3 or 4 times)
```

After a couple of errors ubuntu gave me an emergency prompt or asked me to hit Ctrl+D to continue boot, which is what I actually did. When finished I got a message telling me that a disk with the specified UUID could not be mounted. This was my /home partition. The uuid designated (under /etc/fstab) for /dev/sda1 was not to be found under /dev/disk/by-uuid. After trying to manually mount **/dev/sda1** in /home I was surprised to found out that it was the NTFS (!) partition that has been actually mount.

What's more I found out that in /dev/disk/by-uuid the specified uuids were pointing to ../mapper/sd<number>. Also there are *NO* hd* devices under /dev. There were hdaX and hdbX when I still had edgy.

Contents of /etc/fstab
```

proc /proc proc defaults 0 0

UUID=bfb6569c-fcaf-44e2-bfe8-bd6b2e730d85 / ext3 defaults,errors=remount-ro 0 1

UUID=77345119-bc83-4fcb-8c91-ed629ec1e582 /home ext3 defaults 0 2 ## <- This uuid does not exist :-/

UUID=80FC69AFFC699FE0 /media/winC ntfs umask=222,utf8 0 1

UUID=A4B3-39B4 /media/winD vfat defaults,utf8,umask=007,gid=46 0 1
/dev/hdb2 none swap sw 0 0 ## <- This one can not be found too. No /dev/hd*
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0 <- Same as above

```

I could *really* use some help here, please. The fact that I do not know who's the actually "culprit" for this problem leads me to a dead end.

**Edit 1**: Just a minor update. It seems that all hdX devices are "changed" to sdX respectively. As a result hda moved to sda and hdb to sdb. As a result the "old" sda containing the home partition is nowhere to be found. 

**Edit 2**: **Using 2.6.17-10 kernel (last kernel in edgy) seemed to boot the system just fine. Problem seems to be caused by the 2.6.20-15 kernel in feisty.  Is there a way to use the 2.6.20 kernel??**

Thank you in advance

---

### Post by FuturePast on 2007-05-12
To start, you can safely remove mdadm.

Also, can you post the results of lspci?

---

### Post by Foucault on 2007-05-12
I've removed mdadm and now I can't even boot from 2.6.17 kernel. Same thing as before,* but now there are no **sdX** devices under /dev*. Only hdX. Strange, isn't it? Again I can't find my (correct) /dev/sda1 partition. Reinstalling mdadm again had no result. Either I am doing something wrong or something else went very bad during update. Any further help would be much appreciated.

---

### Post by gdcondor on 2007-05-13
i've exactly the same pb : upgrading from edgy to feisty moved all my /dev/hdX partitions to /dev/sdX and it's completely messy
i noticed this because the system didn't mount the swap partition anymore :( imagine the mess :( i managed to mount it with gnome partition editor, but gnome partition editor doesn't find where my partition /home is mounted (but it's mounted and working !)

any idea ?

---

### Post by Pragmatist on 2007-05-27
Please, both of you, post outputs to these commands.:

```
mount
``````
cat /etc/fstab
```This next command will create a file  called "mygrub.txt" Please post it as an attachment:

```
cat /boot/grub/menu.lst >> mygrub.txt
```

Edit:  Since there is more than one person, better filenames would be <username>_grub.txt  So, f**oucault_grub.txt**  and **gdcondor_grub.txt**

---

### Post by brendanh on 2007-05-29
Same sort of problem here. Basically upgraded 6.04 to 6.1 and then to 7.04 with Update Manager. All works well except fstab has been altered and old locations are not there any more, namely / has been modified to /dev/sda1 (and not /dev/hda1) which therefore screwd up some other dev locations to usb hard drives and such.

Text files of 'cat /etc/fstab' and 'cat /boot/grub/menu.lst' and 'mount' attached for your reference.

Unsure if it matters but there were lots of mdadm errors while doing the 6.1 to 7.04 upgrade. No RAID devices set up here, just 1 IDE hard drive and 2 IDE DVD burners.

I have not attempted to fix this yet as this is a production machine with multiple samba shares. All solutions appreciated.

Regards,
brendanh

---

