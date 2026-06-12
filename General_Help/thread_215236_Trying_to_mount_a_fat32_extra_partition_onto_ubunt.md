---
title: "Trying to mount a fat32 extra partition onto ubuntu"
date: 2006-07-13
forum: General Help
---

### Post by shickidyshade on 2006-07-13
Ok I have three partitions on my computer a windows, an empty, and ubuntu I am trying to mount the second onto my ubuntu desktop I am using the help of [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) but i am still need help
here are the partitions on my computer
I believe i want to mount the /dev/sda3 onto ubuntu

shade@VU25644:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        3852    30876930    7  HPFS/NTFS
/dev/sda3            3853        6116    18185580    c  W95 FAT32 (LBA)
/dev/sda4            6117        7296     9478350    5  Extended
/dev/sda5   *        6117        7243     9052596   83  Linux
/dev/sda6            7244        7296      425691   82  Linux swap / Solaris

So then i follow and attempted to edit the fstab file 
and this is what i see 



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



does anybody have any ideas of how to edit this

thaks

---

### Post by Dr. Nick on 2006-07-13
the guide goes into that aswell, I will give what I think may work specifically for you though, Some of this is word for word off the link

make a mount point, this is where you will get the files that are on the fat32 drive

sudo mkdir /*whateveryouwant*

then

Now, we need to edit the /etc/fstab file to make the Windows partition mount with the proper permissions (NTFS is read-only in Ubuntu). First, let's make a back-up copy of the /etc/fstab file:
 
sudo cp /etc/fstab /etc/fstab_backup


Next, let's edit the fstab file:
 
sudo nano /etc/fstab

add this line

[B]/dev/sda3 /whatever_you_called_above_folder vfat iocharset=utf8,umask=000 0 0

[/B] When you're done editing the /etc/fstab file, save (Control-X), confirm (y), and exit (Enter). 
 Finally, we'd remount them both:
sudo mount -a

---

### Post by freshanointing on 2006-07-22
Great i had same problems and it worked!

---

### Post by redbluemangle on 2006-11-05
very helpful, thankyou!

---

