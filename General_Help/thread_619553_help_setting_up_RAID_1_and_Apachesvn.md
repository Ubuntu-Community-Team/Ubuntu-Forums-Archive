---
title: "help setting up RAID 1 and Apache/svn"
date: 2007-11-21
forum: General Help
---

### Post by agentdz015 on 2007-11-21
I'm using ubuntu 7.10, and am a bit new to this...  Firstly - is this the right place for this?  I also noticed there's an "instalation and upgrades" section... but wasn't sure if that was just for OS installs....  let me know if I'm categorizing wrong.

Ok - I've tried several step-by-step guides online and so far no luck... I'm trying to do two tasks:

1 - set up raid 1 on my computer's 2nd and 3rd hard drives
2 - set up apache / svn

Do you have any guides you can recommend to me for either of these tasks?  Then when I have trouble (hopefully not...? but probably...) I can come back and get a consult! :-P

thanks all!

---

### Post by Linteg on 2007-11-21
I can help you with the raid, but, this presumes you know at least a little about your hardware (their dev-addresses) and that you are not afraid of the terminal. 

First you have to format the drives, use cfdisk (or gparted if you want a gui tool) to create one partition on each of the drives (the partitions must have equal size, but if the drives are identical that won't be a problem). Presuming your two hdd:s are /dev/sdb and /dev/sdc, run:
```
sudo cfdisk /dev/sdb
sudo cfdisk /dev/sdc
```
delete any previous partitions and create a new one, as big as you like (as long as both partitions are of equal size) and write the partition table.
**Be careful**, formatting the wrong disk (e.g. one with files you want to keep) **will lead to data loss.**
You should also create/decide a mountpoint for your array (e.g. /mnt/myraidarray)

The easiest thing to use is linux' own software raid, and for that, you will need to install mdadm.
```
sudo apt-get install mdadm
```
The installation might ask a few questions, but they shouldn't be too hard (e.g if you want to boot from the md devices or not etc), the installation/boot scripts should also make sure that the proper modules are loaded at boot.

Onc mdadm is installed create a new raid array with
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1
```
If mdadm complains about a missing kernel module, run:
```
sudo modprobe raid1
```
and try the previous step again. Now the drives will sync, and that might take some time, you can check the progress with
```
sudo cat /proc/mdstat
```
or get information about the array with
```
mdadm --misc --detail /dev/md0
```

When this is done your raid array, all you need to do now is to create a file system on it. Note: íIn the following examples i'll presume that you chose jfs, if you chose another file system, replace jfs with ext3/xfs/reiserfs
```
sudo mkfs.jfs /dev/md0
```

So, try to mount it!
```
sudo mount /dev/md0 /mnt/myraidarray -t jfs
```
If there are no errors, open your favourite editor and edit /etc/fstab
```
sudo gedit /etc/fstab
```
and add the following line
```
/dev/md0  /mnt/myraidarray  jfs  defaults  0 0
```
You might want to change the last 0 to 2, this will make sure that the file system is checked at boot if your computer was shut down before it had unmounted the drive, some file systems such as jfs requires file system checks in such cases.

Now we're done. It could be wise to check that /etc/mdadm.conf has a line which looks omething like this:
```
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=b6065276:860e04ff:43df5364:f4db0f8c 
```
if not, create it with
```
sudo -s
mdadm --examine --brief --scan --config=partitions >> /etc/mdadm.conf
exit
```
If you ever lose your mdadm.conf, all you have to do make to run the previous command to restore it, followed by a
```
mdadm --assemble --scan
```
to reassemble your drives (start the array).

Feel free to comment or ask any questions.

(Parts of this guide have been taken from/inspired by a post in [ArchLinux' Wiki](http://wiki.archlinux.org/index.php/Installing_with_Software_RAID_or_LVM))

---

