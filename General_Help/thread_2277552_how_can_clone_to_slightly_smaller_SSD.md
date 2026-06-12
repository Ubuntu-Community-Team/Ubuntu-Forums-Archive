---
title: "how can clone to slightly smaller SSD"
date: 2015-05-09
forum: General Help
---

### Post by odror on 2015-05-09
I have a 512GB SSD

I would like to clone it to a 500GB SSD.

I removed the swap partition. There is plenty of space in the new (slightly smaller SSD).

Clonezilla will not clone it. Is there another way to clone it. In particular I would like to preserve the UEFI boot partition. and the Main Unix partition. I would like the new disk to boot in the same computer seamlessly without the air of boor-repair.

my Disk layout is as follows :
/dev/sdb1   fat32 /boot/efi  512MB
/dev/sdb2   ext4  /, /var/lib/docker/aufs    460GB
/dev/sdb3    swap     165.62gb

if it make any difference there are additional w8 (UEFI) partitions in /dev/sda.  /dev/sdb1 is the first boot partition.

Thanks

Any help will be appreciated.

---

### Post by oldfred on 2015-05-09
Are you sure you are booting from the efi partition on the sdb drive. I have had major issues getting grub to install to sdb. (The only way was to disconnect sda.)

And the efi partition requires not install, you can just copy it.
And swap is easy to delete and recreate, as it has no data. Just you have to edit fstab in new drive with new swap's UUID.

Does it really say 165GB for swap?? I normally suggest 2GB for anyone with 4GB of RAM or more.
       [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by odror on 2015-05-09
The swap only only 16gb

Yes I am sure that the Linux partition is the First partition to boot.

Windows has its own UEFI partition  at /dev/sda

---

### Post by oldfred on 2015-05-09
I prefer new install over copy/clone. 
Most that do copy use clonezilla, but I never have used it. Some have just used rsync or cp -a to preserve ownership & permissions.

I prefer new install, but you have to copy /home to have all your settings & data and export a list of installed applications to make it easy to reinstall them. My backup assumes new install, so it includes everything I think I need.

If copying data, you can exclude the same files that are not useful & should houseclean thoroughly before copying.

       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

            Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

    
       Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:

---

### Post by odror on 2015-05-09
I actually need to clone the disk so that I swap them seamlessly.  I need to do that prior to the 15.04 upgrade. if there is going to be an issue with the upgrade, I can back to 14.10.

I have too many setting. Fresh install will consumes too much time.

---

### Post by oldfred on 2015-05-09
Even on my first SSD that was only 64GB, I created 2 / (root) partitions so I could have two different installs. One main working and one for testing or upgrades. I kept /home inside / but had all data on a HDD.
With my new system and a 128GB SSD, I do not know what to do with all the space. All data is still on hard drive, but I do not have Windows consuming space.
```
/dev/sda3        24G   13G   11G  54% /
/dev/sda1       500M   13M  487M   3% /boot/efi

```

---

