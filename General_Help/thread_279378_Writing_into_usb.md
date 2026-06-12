---
title: "Writing into usb"
date: 2006-10-17
forum: General Help
---

### Post by Andrea_44 on 2006-10-17
Hi,

I pluged in an usb drive to ubuntu, and it allows me to read and write into it.

But when I mount the usb drive into Debian, it only allow me to read.
I did "mount /dev/sda1 /mnt/usb"

When I tried to put a file into the usb, it "no permission to write to this folder".
I have tried "chmod 777 /mnt/usb"

Is there any flag I need to set when mounting in order to write on to the usb?

Many Thanks,

Andres

---

### Post by aysiu on 2006-10-17
Theoretically external USB should just automount with the proper permissions.

Your situation is not common, but it's also not unheard of.

Can you plug the drive in and then post back here the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by Andrea_44 on 2006-10-17
My usb is /dev/sdb1. 

"sudo fdisk -l" : return nothing

"fdisk -l /dev/sdb1" :
Disk /dev/sdb: 1027 MB, 1027604480 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         125     1003488+   e  W95 FAT16 (LBA)
Partition 1 has different physical/logical endings:
     phys=(123, 254, 63) logical=(124, 237, 49)

"df -h" : 
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              18G  2.1G   15G  13% /
tmpfs                 125M     0  125M   0% /dev/shm
/dev/sda1             980M  788M  192M  81% /mnt/removable
/dev/sdb1             980M  788M  192M  81% /mnt/removable

cat /etc/fstab:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by meng on 2006-10-17
I wonder if the problem is your user's membership of groups. That said, I'm not sure which group/s you need to be a member of. usb is the most obvious I guess, but I could be wrong.

---

### Post by aysiu on 2006-10-17
This seems to be your problem: ```
Device Boot Start End Blocks Id System
/dev/sdb1 * 1 125 1003488+ e W95 FAT16 (LBA)
**Partition 1 has different physical/logical endings:**
phys=(123, 254, 63) logical=(124, 237, 49)
```

---

### Post by Predius on 2006-10-17
Can you trying using sudo to copy something?

---

### Post by Andrea_44 on 2006-10-17
> Can you trying using sudo to copy something?

yes, I have just realised that I can copy stuff using sudo.

I just can't drag and drop files to my mount point "/mnt/usb" like in ubuntu.

Can I change the permission of the "/mnt/usb"?

---

