---
title: "Mount on startup"
date: 2008-02-26
forum: General Help
---

### Post by psychofish25 on 2008-02-26
I am currently dual-botting Ubuntu 7.10 and Windows Vista. I want my computer to mount my Vista HD (named COMPAQ) when I startup my computer. I was wondering where my COMPAQ HD is located so I can use the mount command in a shell script. Also, where can I edit what programs start on startup?

---

### Post by dark_phantom on 2008-02-26
If you only have one disk then it should already be there.  Something like, /dev/sda2 or similar.  Do an ls to confirm that it's there.  You can mount it to something like /windows via /etc/fstab.

---

### Post by psychofish25 on 2008-02-26
Well the drive shows up, but I can't get info until I mount it. I like where it is now. Could someone explain it a different way? I'm kinda of new to Linux.

---

### Post by dark_phantom on 2008-02-26
I'm confused, is it a usb drive?  I also have dual booting on all of my PCs and they're mounted automatically.  Can you post your output of these two commands?

ls /dev/sd*
df -khl
mount

Edit:  Take a look at this [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131).

---

### Post by psychofish25 on 2008-02-26
> **dark_phantom said:**
> I'm confused, is it a usb drive?  I also have dual booting on all of my PCs and they're mounted automatically.  Can you post your output of these two commands?

ls /dev/sd*
df -khl
mount

HD=hard drive

```
jordan@Jordan-PC:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda3  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5
jordan@Jordan-PC:~$ df -khl
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             288G   14G  260G   5% /
varrun               1014M   96K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   96K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0              33M   33M     0 100% /media/cdrom0
/dev/sda1             142G   76G   67G  54% /media/COMPAQ
jordan@Jordan-PC:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=jordan)
/dev/sda1 on /media/COMPAQ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
jordan@Jordan-PC:~$ 

```

---

### Post by dark_phantom on 2008-02-26
> **psychofish25 said:**
> 

```
jordan@Jordan-PC:~$ ls /dev/sd*
/dev/sda  /dev/sda1  /dev/sda3  /dev/sdb  /dev/sdb1  /dev/sdb2  /dev/sdb5
jordan@Jordan-PC:~$ df -khl
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             288G   14G  260G   5% /
varrun               1014M   96K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   96K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   34M  980M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/scd0              33M   33M     0 100% /media/cdrom0
[color=red]/dev/sda1             142G   76G   67G  54% /media/COMPAQ[/color]
jordan@Jordan-PC:~$ mount
/dev/sdb1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/scd0 on /media/cdrom0 type iso9660 (ro,nosuid,nodev,user=jordan)
[color=red]/dev/sda1 on /media/COMPAQ type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)[/color]
jordan@Jordan-PC:~$ 

```

Highlighted in [color=red]red[/color] is your vista partition.  It should already be in your /etc/fstab.  Grep for it -> grep sda1 /etc/fstab and look for the UUID in /dev/disk/by-uuid/.

It should look something like this:
UUID=84D43463D4345A1E /media/sda2     ntfs    defaults,umask=007,gid=46 0       1

If not, then enter it in fstab like how it is above.
UUID="# from  /dev/disk/by-uuid/" /media/COMPAQ  ntfs defaults,umask=007 0 0

The UUID should be that which points to sda1.

---

### Post by sadeghi on 2008-02-27
Hi
choose the device & partition you would like to be mounted at start up.
use these commands to see what is your device name:

sudo gparted
sudo fdisk -l

you should modify /etc/fstab and insert a line for that device, you can use device address (e.g. /dev/sda1) or UUID. To see what is UUID of that partition use:

sudo vol_id /dev/sda* --uuid
(instead of * use number of your partition from past steps e.g. sda1,sda2,...)

open fstab as root user:

sudo gedit /etc/fstab

insert this line at the bottom or anywhere:

#REMEMBER! you should replace your own UUID
#[comment]: /dev/sda5
UUID=CCA4D0EBA4D0D952 _/media/sda5_     ntfs    defaults,umask=007,gid=46 0       1

The underlined words are the folder address that you'd like to mount the storage device
if you want your partition to be mounted even if you had a broken shutdown at vista you should se something like this:

#I have used device address instead of uuid here
/dev/sda5_ /media/sda5_ ntfs-3g defaults,force 0 0

The underlined words are the folder address that you'd like to mount the storage device
Hope these help you.

---

