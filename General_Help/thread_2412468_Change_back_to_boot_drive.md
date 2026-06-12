---
title: "Change back to boot drive"
date: 2019-02-13
forum: General Help
---

### Post by ordak on 2019-02-13
Hi,

I had Ubuntu 16.04 and a boot partition. After upgrade to 18.04 , kernels seem to be placed in the "bigger volume". How can I go back to UEFI in the previous drive ?

---

### Post by Impavidus on 2019-02-13
We need some details on your system's configuration:```
df -h
sudo parted -l
cat /etc/fstab
```

BTW, when you don't really need a /boot partition (you need it when using an encrypted system), it's better not to have one.

---

### Post by yancek on 2019-02-13
What "bigger volume"?  If you did an upgrade from an earlier version, Ubuntu would be on the same / partition.  I would expect that if you did an upgrade, the Ubuntu EFI files for the new system would replace the files on the EFI partition and the / partition.  In addition to posting the output of the commands suggested above, you might try running boot repair with the Create BootInfo Summary option, using the 2nd option suggested on the page to use the ppa and post the link you get when finished.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ordak on 2019-02-14
> **Impavidus said:**
> We need some details on your system's configuration:```
df -h
sudo parted -l
cat /etc/fstab
```

BTW, when you don't really need a /boot partition (you need it when using an encrypted system), it's better not to have one.


```

 df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         3.9G     0  3.9G   0% /dev
tmpfs                        787M  1.9M  785M   1% /run
/dev/mapper/ubuntu--vg-root  909G   42G  821G   5% /
tmpfs                        3.9G   23M  3.9G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0                   4.8M  4.8M     0 100% /snap/network-manager/355
/dev/loop1                   2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop3                   3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop11                  2.3M  2.3M     0 100% /snap/gnome-calculator/222
/dev/loop13                   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop14                   13M   13M     0 100% /snap/gnome-characters/117
/dev/loop17                   15M   15M     0 100% /snap/gnome-logs/45
/dev/loop16                   13M   13M     0 100% /snap/gnome-characters/139
/dev/loop2                   141M  141M     0 100% /snap/gnome-3-26-1604/70
/dev/loop19                  3.8M  3.8M     0 100% /snap/gnome-system-monitor/54
/dev/loop18                  2.3M  2.3M     0 100% /snap/gnome-calculator/238
/dev/loop4                    90M   90M     0 100% /snap/core/6130
/dev/loop20                   35M   35M     0 100% /snap/gtk-common-themes/808
/dev/loop5                    13M   13M     0 100% /snap/gnome-characters/124
/dev/loop21                  4.8M  4.8M     0 100% /snap/network-manager/314
/dev/loop23                  3.8M  3.8M     0 100% /snap/gnome-system-monitor/51
/dev/loop8                   4.8M  4.8M     0 100% /snap/network-manager/379
/dev/loop7                    15M   15M     0 100% /snap/gnome-logs/40
/dev/loop9                    91M   91M     0 100% /snap/core/6350
/dev/loop12                   92M   92M     0 100% /snap/core/6259
/dev/loop10                   15M   15M     0 100% /snap/gnome-logs/43
/dev/loop15                  141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/sda1                    511M  6.1M  505M   2% /boot/efi
tmpfs                        787M   32K  786M   1% /run/user/1000
/dev/loop24                  141M  141M     0 100% /snap/gnome-3-26-1604/78
/dev/loop25                   35M   35M     0 100% /snap/gtk-common-themes/1122



```

```

sudo parted -l
Model: ATA ST1000LM035-1RK1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size   File system  Name                  Flags
 1      1049kB  538MB   537MB  fat32        EFI System Partition  boot, esp
 2      538MB   1050MB  512MB  ext2
 3      1050MB  1000GB  999GB                                     lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 8468MB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  8468MB  8468MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 991GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  991GB  991GB  ext4



```

By the way I do not want an encryted system, I just thought default /boot partition is a better chocie.

---

### Post by ordak on 2019-02-14
> **yancek said:**
> What "bigger volume"?  If you did an upgrade from an earlier version, Ubuntu would be on the same / partition.  I would expect that if you did an upgrade, the Ubuntu EFI files for the new system would replace the files on the EFI partition and the / partition.  In addition to posting the output of the commands suggested above, you might try running boot repair with the Create BootInfo Summary option, using the 2nd option suggested on the page to use the ppa and post the link you get when finished.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I have partition1, partition2, partition3 called devices:

/dev/sda1  /dev/sda2 /dev/sda3

first and second are about 500MB, third has 999GB size.

---

### Post by Dennis N on 2019-02-14
Did you do a new install? or use the Software Updater in 16.04? A new install would not mount and use your sda2 for /boot unless you specify this in the installer's partitioning screen.

---

### Post by oldfred on 2019-02-14
You have an LVM install with UEFI booting.
UEFI requires the ESP - efi system partition or your sda1.
And LVM default install uses a separate /boot partition and one more partition for all your LVM logical volumes.
LVM is the default if you select full drive encryption.

LVM is more advanced and often used with server or server type installs. But is also used with full drive encrypted installs. If new user not really recommended unless you have to have encryption. And then you have more to learn as you must then often use LVM tools in addition.

 LVM Advantages/Disadvantages Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)

---

### Post by Dennis N on 2019-02-14
> By the way I do not want an encryted system, I just thought default /boot partition is a better choice.

Well, we can see you didn't get one (a boot partition). What about your /etc/fstab? You quoted that request in your post #4, but never showed the result. It's important to see that. You can do an UEFI install with LVM and without a separate boot partition as long as the OS not encrypted, and that could account for this result. But it's not the default, as I gather.

---

### Post by ordak on 2019-02-15
> **Dennis N said:**
> Well, we can see you didn't get one (a boot partition). What about your /etc/fstab? You quoted that request in your post #4, but never showed the result. It's important to see that. You can do an UEFI install with LVM and without a separate boot partition as long as the OS not encrypted, and that could account for this result. But it's not the default, as I gather.

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=D934-9484  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0



```

---

### Post by Dennis N on 2019-02-15
As expected. If you had a boot partition set up on sda2, there would be a line in here to mount sda2 at /boot. If you used Software Updater to go from 16.04 to 18.04, I would expect it to preserve any separate boot setup. Any upgrades I have done with Software Updater retain the /etc/fstab from the old version with partitions (like my separate data partition) working as before.

What a new install of 18.04 does depends on your choices made when you set up the Installation Type. When I do LVM, I always use the 'something else' option to set up the system, since I don't use a separate boot or encryption. I would have to look at the installer to see what checking the default LVM box does without selecting encryption - I've never tried the default.

Which did you do? Use Software Updater or new install?

---

### Post by Dennis N on 2019-02-15
> I would have to look at the installer to see what checking the default LVM box does without selecting encryption - I've never tried the default.

I followed through on this with an Xubuntu 18.04.1 install in a virtual machine using its UEFI firmware option. Starting the installation, I selected "Erase Disk and Install Xubuntu", then "Use LVM with the new Xubuntu installation". The attached image shows the partitions the installer created for these choices. Notice there is no boot partition.

---

### Post by ordak on 2019-02-16
> **Dennis N said:**
> As expected. If you had a boot partition set up on sda2, there would be a line in here to mount sda2 at /boot. If you used Software Updater to go from 16.04 to 18.04, I would expect it to preserve any separate boot setup. Any upgrades I have done with Software Updater retain the /etc/fstab from the old version with partitions (like my separate data partition) working as before.

What a new install of 18.04 does depends on your choices made when you set up the Installation Type. When I do LVM, I always use the 'something else' option to set up the system, since I don't use a separate boot or encryption. I would have to look at the installer to see what checking the default LVM box does without selecting encryption - I've never tried the default.

Which did you do? Use Software Updater or new install?

I roughly remember I created a bootable usb flash memory 18.04 and upgraded my 16.04 installation because the laptop had sound problems. If according to [this thread]("https://ubuntuforums.org/showthread.php?t=2411808"), every time I have to see a grub menu in turn on, I want to reactivate my /boot partition.

---

### Post by Dennis N on 2019-02-16
If you installed from a USB with the 18.04 installer, since there was an OS already there, the installer might offer to replace the existing OS. Unless you used the "something else" option to set up the mount point for the separate boot partition, the installer wouldn't do that automatically. It didn't erase the old boot partition either, so its still there as sda2. 

Your boot files are now written into the logical volume vg-root, not sda2. The choice to use a separate boot partition has to be made on installation.

Grub was recently changed. From now on, we are going to get a grub menu in our UEFI systems when we start up. There is no way to skip it. The delay at the grub menu now defaults to 30 sec instead of 10 sec, so just press enter at the grub screen to skip the 30 sec wait.

---

