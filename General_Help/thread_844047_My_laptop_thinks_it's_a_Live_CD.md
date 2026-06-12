---
title: "My laptop thinks it's a Live CD"
date: 2008-06-29
forum: General Help
---

### Post by uzd4ce on 2008-06-29
Ok, I'm an idiot sometimes.  I was trying to install Ubuntu EEE on my EEEPC 900 and ended up borking my other laptop (which dual boots Hardy and XP).

I was attempting to run this script to get the .iso onto my thumbdrive.
```
sudo apt-get install syslinux
wget http://startx.ro/sugar/isotostick.sh
chmod +x isotostick.sh
sudo umount /dev/sdX1
sudo mkfs.vfat -F 32 -n ubuntueee /dev/sdX1
sudo parted /dev/sdX set 1 boot on
sudo ./isotostick.sh image.iso /dev/sdX1 
sudo syslinux /dev/sdX1

```

But instead of pointing it at dev/my thumbdrive, I ran the script at my main hard drive.

Everything was fine for several days until I had to reboot and it booted straight to Ubuntu EEE, no stop for GRUB or anything.

I tried to boot from a regular Hardy Live CD, but it always goes straight to the Ubuntu EEE install.

Once it boots, I can see my regular Ubuntu partition, which I think is marked as /media/disk rather than root, but I don't know how to fix it.

Anyone have any ideas?

Thanks

---

### Post by fahadsadah on 2008-06-29
Please can you post the outputs of: 
```

cat /etc/mtab
cat /etc/fstab
sudo fdisk -l

```

---

### Post by uzd4ce on 2008-06-29
Here's the output

```
ubuntu@ubuntu:~$ sudo cat /etc/mtab
proc /proc proc rw 0 0
sysfs /sys sysfs rw 0 0
tmpfs /lib/modules/2.6.24-16-generic/volatile tmpfs rw,mode=0755 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ubuntu/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ubuntu 0 0
/dev/scd0 /media/Ubuntu\0408.04\040i386 iso9660 ro,nosuid,nodev,uhelper=hal,uid=999,utf8 0 0
/dev/sda3 /media/disk ext3 rw,nosuid,nodev,uhelper=hal 0 0


ubuntu@ubuntu:~$ sudo cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        2608    20852370    7  HPFS/NTFS
/dev/sda3            2609       19111   132560347+  83  Linux
/dev/sda4           19112       19457     2779245    5  Extended
/dev/sda5           19112       19457     2779213+  82  Linux swap / Solaris



```

Thanks

---

