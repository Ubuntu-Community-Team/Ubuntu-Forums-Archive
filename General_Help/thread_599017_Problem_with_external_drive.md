---
title: "Problem with external drive"
date: 2007-10-31
forum: General Help
---

### Post by ascus4 on 2007-10-31
I have an external, USB harddrive that I use for backups.  It won't mount any longer.
I may not have unmounted it the last time I used it.  Either that or something else is wrong.

Anyway, when I plug it in to the USB I get the error:  
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sda1: Operation not suported Mount is denied because NTFS is marked to be in use.

It then tells me to enter the following on the command line to force a mount:
mount -t ntfs-3g /dev/sda1 /media/simpledrive -0 force

I entered that and it returned error:
$LogFile indicates unclean shutdown (0,0) WARNING: Forced mount, reset $logfile.  Fuse: failed to access mountpoint /media/simpledrive: No sucu file or director.  FUSE mount point creation failed.  Unmounting /dev/sda1 (simpledrive).

Is there a way I can get this thing mounted?

Help?

Thanks in advance.

---

### Post by trak87 on 2007-10-31
This will sound so Windowish, but have you tried a reboot?

---

### Post by ascus4 on 2007-11-01
I have rebooted.  It didn't help.

---

### Post by StefanPieter on 2007-11-01
I'm having the same problem.

---

### Post by ascus4 on 2007-11-01
Ok, I got it.  You said to reboot and I had just done a fresh start so I said I had but...
I rebooted after I got the error and it mounted just fine.

Actually, the karma gods like to mess with me.  I figured that if I wrote that a reboot didn't work, then that would cause it to work after a reboot.

---

### Post by Graeme2804 on 2007-11-01
Well, I get the same problem, except when I try to mount it says 'only root can do this'.

I tried to log in with root and it said 'Administrator account can not log in from this screen' or summat like that.

Anyone know where to log in as root?

---

### Post by petteriIII on 2007-11-01
> **Graeme2804 said:**
> Well, I get the same problem, except when I try to mount it says 'only root can do this'.

I tried to log in with root and it said 'Administrator account can not log in from this screen' or summat like that.

Anyone know where to log in as root?

You try to mount it to a directory owned by root. Give the following command: sudo chown username:usergroup /<the directory you are trying to mount>.

---

### Post by trak87 on 2007-11-01
I don't know if any of this will help, but perhaps the following will explain the cryptic mount command to some. For example, to mount a drive one might do this:

```
sudo mount -t ntfs-3g /dev/sda1 /media/simpledrive
```

Here's the breakdown:

**sudo** = execute the following command as root. Only root can do certain system things, so this is often important when working with the system as a whole as opposed to working only inside your home directory.

**mount** = the command to "hook up" the drive and make it accessible to the user(s) via some directory.

**-t** = the type of filesystem you are trying to mount. In this case it's a drive formatted with the  Microsoft ntfs filesystem. We're using the **ntfs-3g** driver as opposed to the regular ntfs driver.  It could also be many other options like ext3 or ext2 or vfat (fat32) or msdos (fat16), etc. It just depends of what filesystem the drive was formatted with, but it will generally be ext3 for Linux and either ntfs or vfat (fat32) for Windows.

**/dev/sda1** = The drive partition you are trying to mount. The /dev part will stay the same, but the sda1 could be different depending on which drive and which partition on that drive is the one you are trying to mount. It may be /dev/sda1 or /dev/sda2 or /dev/sdb7 or /dev/hda5. sda generally means the first scsi or sata drive. sda1 means the first partition on the first drive. sdb9 would mean the ninth partition on the second drive. hda means an older style IDE (also called PATA) drive. To figure out which partitions you have you can run *mount* by itself or *df -h* or view the /etc/fstab or /etc/mtab files.

**/media/simpledrive** = the starting directory on your system that you want to be able to access this drive. This would be the directory that you surf to via Nautilus or the command line. This directory needs to exist prior to using the mount command! Sometimes Ubuntu creates this directory automatically when you use a removable drive like a USB  drive. Other times you need to create the directory with *sudo mkdir /media/somedirectoryname*.

For more info, type *man <command>* at the command line to get lots of information. In this case, type *man mount* .


To unmount a drive use the umount command. Note the unusual spelling: UMOUNT and NOT unmount. It is a lot easier to use once a drive is mounted. In the above example, either one of these commands would work:

```
sudo umount /dev/sda1 
```

or 

```
sudo umount /media/simpledrive
```

---

### Post by bagbiter on 2007-11-03
that was really helpful, trak87..! nice one :)

i have one problem though. it seems everytime i disconnect my external ntfs-drive and try to connect it again, i have to manually mount in terminal again, and each time the /dev/sdXX changes.. like sometimes it's sdb1 and others sdc1 or sda1.. any way to fix this?

---

