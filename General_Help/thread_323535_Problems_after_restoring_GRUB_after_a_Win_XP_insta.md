---
title: "Problems after restoring GRUB after a Win XP installation..."
date: 2006-12-22
forum: General Help
---

### Post by informer2000 on 2006-12-22
I've been using Ubuntu Linux Breezy Badger 5.10 for about 8 months or so and have been really satisfied and enjoying it up to the point where I had to re-install Win XP for a task that required VS.NET 2005. Of course, Windows overwritten the MBR and GRUB no longer loads.

I've installed SystemRescueCD on my USB stick and booted to a shell, created **/mnt/mymount**, mounted **/dev/hda3**, and listed the contents to make sure that this is the partition for the kernel. I changed root to the new mounted point and accessed the shell. I tried to re-install grub using "**grub-install /dev/hda**" and this time (after adding some options that explicitly specifies where GRUB files are located) instead of getting the error "The file /boot/grub/stage1 not read correctly" I got the prompt once again. So, I rebooted and GRUB did load up to stage 1.5 but then suddenly reboots the PC again and so on. Using "**setup (hd0)**" from the GRUB shell completed successfully but resulted in the same symptoms. Could stage2 be corrupt or something?!


I'm really confused! What's going wrong? I think I did everything correctly. But then again I could be wrong. After all, I am kind of new to the Linux world. I've searched everywhere online but with no luck. Is there a way to restore GRUB again successfully so I can access Ubuntu?


The following may be helpful in determining the cause:

1. Output of "fdisk -l" from the SystemRescueCD shell:
========================================

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1219     9791586    c  W95 FAT32 (LBA)
/dev/hda2            1220        1281      498015   82  Linux swap / Solaris
/dev/hda3            1282        1920     5132767+  83  Linux
/dev/hda4            1921        9729    62725792+   f  W95 Ext'd (LBA)
/dev/hda5            1921        4056    17157388+   b  W95 FAT32
/dev/hda6            4057        6893    22788171    b  W95 FAT32
/dev/hda7            6894        9729    22780138+   b  W95 FAT32

Disk /dev/sda: 262 MB, 262144000 bytes
17 heads, 32 sectors/track, 941 cylinders
Units = cylinders of 544 * 512 = 278528 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         942      255983+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(1000, 16, 32) logical=(941, 2, 31)
```


2. Output of "mount" from the SystemRescueCD shell:
========================================

```
tmpfs on / type tmpfs (rw)
/dev/root on /initrd type ext2 (rw,nogrpid)
/sys on /initrd/sys type sysfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw)
udev on /initrd/dev type tmpfs (rw)
/newroot/dev/sda1 on /mnt/cdrom type vfat (ro)
/dev/cloop on /mnt/cloop type ext2 (ro)
tmpfs on /mnt/cloop/lib/firmware type tmpfs (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
udev on /dev type tmpfs (rw,nosuid)
devpts on /dev/pts type devpts (rw)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw,devmode=0664,devgid=85)
```


3. Output of "mount" from the mounted point's (my original system) shell:
=====================================================

```
/dev/hda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /dev type tmpfs (ro)
```


4. Contents of "fstab" from the mounted point's (my original system) shell:
=====================================================

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     vfat    defaults,umask=000,rw,uid=informer2000,gid=informer2000        0       0
/dev/hda5       /media/hda5     vfat    defaults,umask=000,rw,uid=informer2000,gid=informer2000        0       0
/dev/hda6       /media/hda6     vfat    defaults,umask=000,rw,uid=informer2000,gid=informer2000        0       0
/dev/hda7       /media/hda7     vfat    defaults,umask=000,rw,uid=informer2000,gid=informer2000        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0
//10.0.0.2/c    /home/informer2000/mounts/sliders-2_c    smbfs    credentials=/etc/cred,uid=informer2000,gid=informer2000    0    0
//10.0.0.2/d    /home/informer2000/mounts/sliders-2_d    smbfs   credentials=/etc/cred,uid=informer2000,gid=informer2000 0       0
//10.0.0.2/e    /home/informer2000/mounts/sliders-2_e    smbfs   credentials=/etc/cred,uid=informer2000,gid=informer2000 0       0
//10.0.0.2/f    /home/informer2000/mounts/sliders-2_f    smbfs   credentials=/etc/cred,uid=informer2000,gid=informer2000 0       0
//10.0.0.2/g    /home/informer2000/mounts/sliders-2_g    smbfs   credentials=/etc/cred,uid=informer2000,gid=informer2000 0       0
```


5. Output of "fdisk -l" from the mounted point's (my original system) shell:
=====================================================
```
cannot open /proc/partitions
```

---

### Post by informer2000 on 2006-12-25
Anyone ?!! ](*,)

---

### Post by Vox754 on 2006-12-25
I don't really know how to solve your problem.

Just some advice:
1. Too much code tends to scare people away.
2. I've always read that you should install Windows first, and then any other Operating System. As you just experienced, Windows rewrites the Master Boot Record causing you every sort of troubles.

Better install Windows, leave it there in case you ever need it, and then install Linux in other partitions.

I think this question has been answered hundreds of times in these forums. Just do a quick search.
Some of the results may be two years old, but they are the basis of all this, and still work.

[http://ubuntuforums.org/search.php?searchid=11725405](http://ubuntuforums.org/search.php?searchid=11725405)
[http://ubuntuforums.org/search.php?searchid=11725454](http://ubuntuforums.org/search.php?searchid=11725454)

---

### Post by informer2000 on 2006-12-25
Thanks for the reply **Vox754**.

> 1. Too much code tends to scare people away.

I only wanted to clarify the situation and provide necessary information so that others could help.

> Better install Windows, leave it there in case you ever need it, and then install Linux in other partitions.

The problem with this scenario is that Windows always gets messed up and needs re-installation. 

> I think this question has been answered hundreds of times in these forums. Just do a quick search.

Been there, done that. However, it just doesn't work as expected and as is the case with many users who resolved their problems. My problem is that after restoring GRUB it starts loading when the PC is started but then reboots automatically at stage 1.5 without any notice or reason.

I've read in another forum about a similar situation which eventually was traced down to the BIOS having some sort of program that prevented GRUB from functioning correctly because it was holding back the MBR or something, I'm not sure. But looking at my motherboards BIOS, nothing seems to be related to the MBR in anyway. I have Gigabyte 945G motherboard by the way.

> Some of the results may be two years old, but they are the basis of all this, and still work.

[http://ubuntuforums.org/search.php?searchid=11725405](http://ubuntuforums.org/search.php?searchid=11725405)
[http://ubuntuforums.org/search.php?searchid=11725454](http://ubuntuforums.org/search.php?searchid=11725454)

Some how the links are not working. I get:

*"Sorry - no matches. Please try some different terms."*


One last thing, I tried booting the kernel manually from the GRUB shell from SystemRescueCD and also using the GRUB shell after changing root. However, I get the following error when attempting **initrd**:

```
error 16: inconsistent file system structure.
```

I hope this might help someone guide me to the right direction...

---

### Post by jasonlfunk on 2006-12-25
You might try Super Grub ([http://supergrub.forjamari.linex.org/download.php](http://supergrub.forjamari.linex.org/download.php)) It is a bootable CD that has a lot of featuring including restoring Grub after a Windows Install.

---

