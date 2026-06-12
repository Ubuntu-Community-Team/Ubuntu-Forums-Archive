---
title: "fstab not mounting on startup"
date: 2006-12-17
forum: General Help
---

### Post by Johnny_disco on 2006-12-17
Hi there,

I am using a combined frontend/backend MythTV setup on Server Edgy following the howto guide.  Everything is fine except I am storing my Xvids on an external USB Seagate Hard Drive, it was not auto mounted at startup to I edited fstab, the line in red is the one I added:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2cb0878d-615e-41a9-9941-1d88e00b8e28 /               ext3    defaults,erro$
# /dev/sda3
UUID=52921c50-fff8-4afe-a2e0-48d73bc9e66f /var/lib        xfs     defaults     $
# /dev/sda2
UUID=f7ef2826-0de8-4097-adb9-5e939f622ac1 none            swap    sw           $

[COLOR="Red"]/dev/sdb1       /media/exthdd   vfat    defaults[/COLOR]
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

Now on bootup, my system goes into mythtv directly but I cannot view any videos because the drive is not mounted.  So I have to close.. go to a terminal tyep

"sudo mount -a" and then my password..

then the drive mounts, I reload mythtv and everything is fine but the problem is that I need it to be mounted and ready to roll when I power on.. so any ideas where I have gone wrong?

Thanks

---

### Post by taurus on 2006-12-17
Actually, the line in red should have been

```
/dev/sdb1   /media/exthdd   vfat   defaults,umask=000   0   0
```

---

### Post by Johnny_disco on 2006-12-17
Thanks for the quick response.  I have updated my fstab accordingly as per your guidance but the problem still remains.

I reboot and my mythtv installation boots up, I go into video manager and I cannot start a film.  If I then exit mythtv and open a terminal window I can see my drive with

"fdisk -l"

so I type "sudo mount -a"

then when I go back into mythtv everything is fine and the videos all play perfectly.  It's such a small problem but it's driving me crazy!  I just can't get it to automount...

Thanks

---

### Post by taurus on 2006-12-17
When you first boot up, before running the "sudo mount -a" command, what's the output of this command?

```
df -h
```

---

### Post by Johnny_disco on 2006-12-17
This is what I get:

l
jhorton@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  1.2G  7.6G  14% /
varrun                248M   64K  248M   1% /var/run
varlock               248M     0  248M   0% /var/lock
procbususb             10M  140K  9.9M   2% /proc/bus/usb
udev                   10M  140K  9.9M   2% /dev
devshm                248M     0  248M   0% /dev/shm
/dev/sda3              65G   88M   65G   1% /var/lib

---

### Post by taurus on 2006-12-17
And I assume your USB drive is on and connected before you boot.  What about these two commands (the outputs)?

```
sudo fdisk -l
cat  /etc/fstab
```

---

### Post by Johnny_disco on 2006-12-17
Yes, they work fine if I literally just go to the terminal window and type "sudo mount -a" so yes definitely on and working fine until I reboot then until I type "sudo mount -a" again it's not there!

**sudo fdisk -l** produces this response

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        1309      747022+  82  Linux swap / Solaris
/dev/sda3            1310        9726    67609552+  83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

and **cat /etc/fstab** this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2cb0878d-615e-41a9-9941-1d88e00b8e28 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=52921c50-fff8-4afe-a2e0-48d73bc9e66f /var/lib        xfs     defaults        0       2
# /dev/sda2
UUID=f7ef2826-0de8-4097-adb9-5e939f622ac1 none            swap    sw              0       0

/dev/sdb1       /media/exthdd   vfat    defaults,umask=000      0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by speedman on 2006-12-17
The devices in fstab are mounted before your external drive is recognized by the o/s.  Just add the mount -a command to the end of /etc/init.d/bootmisc.sh.

HTH


SM

---

### Post by Johnny_disco on 2006-12-17
That actually crossed my mind but I didn't know where to place the mount -a command.  I have modified the end of the bootmisc.sh file with "mount -a" but it did nothing.

I tried putting the line at the very end of the file, at the beginning of the file and also just above the final : (colon) of the file.  In addition the guide I followed to install MythTV here:

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

had me create a startup script /usr/local/bin/mythtv.sh

so I added mount -a to that to see if that worked as well.. and it didn't!

Could this be a permission's issue?  If I use a terminal and type "mount -a" I am not allowed, I have to "sudo mount -a".  Could this be an issue?

---

### Post by superm1 on 2006-12-17
> **Johnny_disco said:**
> That actually crossed my mind but I didn't know where to place the mount -a command.  I have modified the end of the bootmisc.sh file with "mount -a" but it did nothing.

I tried putting the line at the very end of the file, at the beginning of the file and also just above the final : (colon) of the file.  In addition the guide I followed to install MythTV here:

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

had me create a startup script /usr/local/bin/mythtv.sh

so I added mount -a to that to see if that worked as well.. and it didn't!

Could this be a permission's issue?  If I use a terminal and type "mount -a" I am not allowed, I have to "sudo mount -a".  Could this be an issue?
Another solution can be to install and start gnome-volume-manager.  If you place it in that script, it will check for usb devices during your sessions.

---

### Post by speedman on 2006-12-17
bootmisc.sh is already running with super user auth, so sudo wouldn't be required there.  However, it's strange that it didn't mount the volume for you.

It's not pretty, but here's an alternative for you ...

Create a script called /usr/local/bin/mountall with your favorite editor.  I'll use gedit as an example:

sudo gedit /usr/local/bin/mountall

Add the following text (not including the dashes):

===== copy below here

#!/bin/bash
# /usr/local/bin/mountall

MT=$(mount|grep sdb1|wc -l)

if      [ $MT -ne 1 ]; then
        mount -a
else    echo "/dev/sdb1 is already mounted";
fi

exit

===== copy above here

Make the mountall script executable:

sudo chmod +x /usr/local/bin/mountall

Then add the line following to the end of /etc/crontab to check the mount status of /dev/sdb1 every 5 minutes and mount if it isn't already mounted:

sudo gedit /etc/crontab

*/5 * * * *   root    /usr/local/bin/mountall &> /dev/null

You could also add a symlink to the mountall script to /etc/rc2.d, which should mount the volume on each boot:

sudo ln -s /usr/local/bin/mountall /etc/rc2.d/S99mountall

HTH


SM

---

### Post by Johnny_disco on 2006-12-18
Sir,

You are a legend!  Worked a treat, made the script, added the symlink and it works now.. boots and I can watch my videos..

Thanks to all.. I cannot praise your assistance enough!

One last question though..  I just copied that parrot fashion and I would like to learn what you did there, is there somewhere you could point me to learn what you just told me to do.  I understand /etc/crontab is something that gets executed all the time but what is the rest of it.. I want to start to understand rather than blindly copying stuff...

Thanks all again, and speedman for taking the time, much appreciated.

John

---

### Post by speedman on 2006-12-18
You can learn more about shell scripting here:

[http://tldp.org/LDP/abs/html/index.html](http://tldp.org/LDP/abs/html/index.html)


SM

---

