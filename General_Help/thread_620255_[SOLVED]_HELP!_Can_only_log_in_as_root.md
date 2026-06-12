---
title: "[SOLVED] HELP! Can only log in as root"
date: 2007-11-22
forum: General Help
---

### Post by viking777 on 2007-11-22
My present version of Gutsy has been very stable for a long while, even when it was a testing version - until today!

For some reason I can only log in as root (I enabled a root account long ago and good job I did or I wouldn't be able to log in at all). If I try to log in as a normal user I just get returned to the log in page again, no explanation as to why.

Logging in to the root account I have tried deleting my user account and recreating it with the same name and have also tried creating a completely new user account with a different name, the result is the same in both cases, I enter the correct username and password at the login screen, it goes away to think about it for a couple of seconds and just returns back to the login page with no error messages or explanations.

WIHIH??

I just don't know how to troubleshoot this.

Luckily I have other distros on the drive that I can use and of course I can still use the root login but Gutsy was my main distribution and I would really like to log in as a normal user not root.

---

### Post by zvacet on 2007-11-22
Boot in recovery mode and type

```
adduser username
```

**username=your user name**

---

### Post by viking777 on 2007-11-22
> **zvacet said:**
> Boot in recovery mode and type

```
adduser username
```

**username=your user name**

Thank you for the reply zvacet, unfortunately it doesn't work. The only response I get when adding my username is that 'username xxxx already exists'. Which is undeniably true as it does exist, a fact confirmed by logging into a root account and looking under 'system settings/user management'

So if anybody else has any other ideas??

---

### Post by viking777 on 2007-11-22
I tried booting into the root account, deleting my user account and then adopting the suggestion above of booting into recovery mode and creating a new account. This works in as much as it does create the account but I still cant log into it. I enter the username and password and just get returned straight to the login window after a couple of seconds.

This is definitely not a password issue, I tried deliberately entering the wrong password and when I do that I get the message 'login failed'. I do not get this message when entering my normal password, it just wont log in??

Anyone??

---

### Post by viking777 on 2007-11-22
There is something really strange going on here, I now note that every utility I use reports that the gutsy partition is full!! This morning it had 10Gb of free space and I haven't copied any data on to it all day.

What is happening here:confused::confused:

---

### Post by aysiu on 2007-11-22
Can you try switching display managers? If you're using Gnome or Xfce, try switching to KDM. If you're using KDE, try switching to GDM.

For example: ```
sudo apt-get update
sudo apt-get install kdm
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm start
```

---

### Post by viking777 on 2007-11-23
> **aysiu said:**
> Can you try switching display managers? If you're using Gnome or Xfce, try switching to KDM. If you're using KDE, try switching to GDM.

For example: ```
sudo apt-get update
sudo apt-get install kdm
sudo /etc/init.d/gdm stop
sudo /etc/init.d/kdm start
```

Thank you for the suggestion aysiu but there is a complication here in that I am running kubuntu not ordinary ubuntu which is probably why gdm installed but wouldn't run.

I have been going over in my  mind exactly what I was doing yesterday that might make this happen, and although I did not put any new data on my Gutsy partition I did move a large amount of data to it temporarily whilst I reformatted another partition. The thing about this is that when I moved it back again it disappeared from the Gutsy partition but didn't reappear on the newly formatted one, in other words it just disappeared. That amount of data is sufficient to fill the Gutsy partition. I put this down to a failure of the reformatting on the original partition, which it may have been, but it doesn't explain where the data has gone to.

I have used du to calculate the size of the data on the partition and it adds up to 7Gb. The partition is 13.6Gb and yet it is reported as being full.

I have also used find to locate any files over 1Gb in size on the partition and there are none that shouldn't be there.

So in other words I seem to have about 6.5Gb of data that cannot be found but seem to exist as far as the OS is concerned.

I have to move to a different distro now because the root account has now become unstable as well, cooling fan running at full speed and random crashes.

Right, I am posting from Hardy now (which is fine) I just ran fsck on the gutsy partition and it was reported as clean, so that is another idea gone.

I'm really stuck here now, dont tell me I have got to reinstall it all.

---

### Post by viking777 on 2007-11-23
Another update.

I have definitely proven that this is a space problem.

I just deleted 800mb of data from my home folder and rebooted and I can now access my user account again and log in normally.

However kdisk free is reporting 152Mb of free space on my gutsy partition whereas du is reporting the total amount of data to be 7Gb which means I should have 6.6Gb of free space:confused:

---

### Post by yota on 2007-11-23
Hi,

probably you have a large portion of disk space reserved to the root user; to check use tune2fs -l like this:
```

root@linbook:/home/yota# tune2fs -l /dev/sda3 |grep Reserved
Reserved block count:     1184191
Reserved GDT blocks:      1018
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)

```
you can alter the dimension of the reserved area with 'tune2fs -m %size' where "%size" is referred to the whole dimension of the filesystem.

Hope this helps!

---

### Post by viking777 on 2007-11-23
> **yota said:**
> Hi,

probably you have a large portion of disk space reserved to the root user; to check use tune2fs -l like this:
```

root@linbook:/home/yota# tune2fs -l /dev/sda3 |grep Reserved
Reserved block count:     1184191
Reserved GDT blocks:      1018
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)

```
you can alter the dimension of the reserved area with 'tune2fs -m %size' where "%size" is referred to the whole dimension of the filesystem.

Hope this helps!

Thanks for the reply yota. The output of the command on my gutsy partition is given below:

tune2fs -l /dev/sda7|grep Reserved
Reserved block count:     181469
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)

That doesn't look too different from your example, but I have zero knowledge of this command and what it does so I am reluctant to change anything in case I make things worse here. Does it look OK to you?

The man pages confuse me even more!!

---

### Post by viking777 on 2007-11-23
OK I threw caution to the wind and set the reserved block size to 5% which I understand is the default. After a reboot the free disk sapce had actually reduced by 1Mb it is now only 152Mb.

So unfortunately this is not the answer.

Anyone else have an idea??

---

### Post by viking777 on 2007-11-23
I ran e2fsck with the -f flag and got the error:

'Filesystem contains large files but lacks LARGE_FILE flag in the superblock'

I elected to fix this, e2fsck completed but again no difference noted still only 7GB of files on 13.6GB partition but only 152Mb reported as free space.

Will I have to reinstall?

---

### Post by viking777 on 2007-11-23
I think I have found my problem although I don't know how to solve it. I have a folder called 'images' in which I keep backups it has a size of 5.6Gb which is exactly the amount of space I am missing and it appears to be both mounted and unmounted at the same time!!

```
umount /mnt/images/
umount: /mnt/images/: not mounted

```

but 

```
   ls /mnt/images/
amended with auto entry.kmy  BOOTWIZ  laptop linux  laptop windows  mozMail

```

if I repeat the same with another partition

```
     umount /mnt/mint/
umount: /mnt/mint/: not mounted
 
```

```
  ls /mnt/mint
#        
```

no response from the terminal because it isn't mounted and yet with images I get the directory contents listed therefore it is mounted even though umount says it isn't. The results are the same in a file manager, the display of the /mnt/mint directory are empty but the display for the /mnt/images directory displays its 5.6G of content.

Therefore it must have been mounted (and counted) twice - but how?

Fstab looks like this:

```
  proc /proc proc defaults 0 0
/dev/sda1 /mnt/windows_c ntfs-3g defaults,locale=en_GB.UTF-8 0 0

/dev/sda5 /mnt/windows_d ntfs-3g defaults,locale=en_GB.UTF-8 0 0
/dev/sda6 /mnt/hardy ext3 defaults 0 0

/dev/sda10   /mnt/images     vfat   rw,auto,user,utf8,umask=007,uid=1000,gid=1000 0       0

/dev/sda8 /mnt/mint ext3 defaults 0 0
/dev/sda11 /mnt/windowsvm ext3 defaults 0 0
/dev/sda7  / ext3 noatime 0 1
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda9 none swap sw 0 0
#usbfs
none /proc/bus/usb usbfs devgid=1001,devmode=664 0 0 
```

dev/sda10 (mnt/images) is only in there once.

mtab looks like this:

```
 /dev/sda7 / ext3 rw,noatime 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
none /proc/bus/usb usbfs rw,devgid=1001,devmode=664 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
 
```

dev/sda10 is not mentioned at all.

Where else can a partition get mounted from??


This is certainly the problem but what can I do about it??

---

### Post by viking777 on 2007-11-23
Simple!!

Just deleted the /mnt/images folder and recreated a folder called 'images'. Mounted it and all is back to normal.

Don't ask me what was going on, it looks as if instead of a link to the real 'images' I had a copy of it instead.

---

