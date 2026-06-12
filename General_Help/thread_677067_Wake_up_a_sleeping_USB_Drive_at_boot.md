---
title: "Wake up a sleeping USB Drive at boot"
date: 2008-01-24
forum: General Help
---

### Post by sonic6567 on 2008-01-24
Hello,

Mythbuntu (ubuntu 7.10)

I have an external USB drive connected to the computer.

I turn the computer on and it boots just fine from the internal hard drive.

If I immediately try to use mythtv to view a video stored on the external usb hard drive it will not work- (mythtv cannot see the hard drive)

I go into the operating system file browser and it shows the usb drive on the left side of the window. I click on the drive and the system naturally accesses it and shows the contents in the right side of the window.

Thats all it takes.  Now the external usb drive is 'awake'.  I can go into mythtv and play videos from it.

--
How do I do this automatically at boot up?  I can't be manually waking up the drive every time I boot up.
--

Thank you

Ben

---

### Post by tekreloaded on 2008-01-24
I think this is the disk not being mounted (mapped to a folder etc...) on startup.
When you open the drive in your file manager, most file managers automatically mount the disk for you.
To automatically mount the disk on startup you can add it to /etc/fstab...
You probably need to add a line like this:
/dev/sda1             /media/usbdrive        auto       noauto,user,sync      0 0

To do this, you can open up the file /etc/fstab in any text editor (for example for gedit on Ubuntu, put into the run box: "gksu gedit /etc/fstab" I think) and add the line shown above.
What you need to replace is /dev/sda1 with the usb drive's filename and /media/usbdrive with wherever the disk should be mounted...

I hope I'm right as I use openSUSE more than Ubuntu - any further suggestions anyone?

EDIT:

To find what you should replace /dev/sda1 with, the easiest way I can think of is to open up a "Terminal" window and type:

mount -l

This will bring up something similar to:

/dev/sdd1 on /media/TekReloaded type vfat (rw,nosuid,nodev,noatime,flush,uid=1000,utf8,shortname=lower) [TekReloaded]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
debugfs on /sys/kernel/debug type debugfs (rw)

What you need to look out for is the label of your disk (mine is TekReloaded)...

Once you have found the line, replace /dev/sda1 with /dev/sdd1 (or similar) and replace /media/usbdrive with /media/TekReloaded (or similar)

---

### Post by sonic6567 on 2008-01-24
Thank you.  I will try this tonight.

---

### Post by tekreloaded on 2008-01-24
:D
Feel free to PM me if you have any problems
:D

---

### Post by sonic6567 on 2008-01-26
well unfortunately this did not work :(

I think it is the right track though.

I edited the /etc/fstab and added the line (substituting my correct values)

reboot - and nothing.  it doesn't work

but I can open a terminal and type:
mount /media/usb_xxx
and poof it works great

if i type:
mount -a
that does not work

The only way is to specifically type:
mount /media/usb_xxx
or
to use the fie manager gui and click on the drive

any thoughts?

---

### Post by osonegro on 2008-01-27
I am having a similar problem and I tried the method described here but no luck.

The comman: mount -l gives me this when the usb drive IS mounted:

oso@KARMA:~$ mount -l
/dev/sdb1 on / type ext3 (rw,errors=remount-ro) []
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/sda1 on /media/sda1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096) [DRIVE_C]
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/My Book type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree) [My Book]

My /etc/fstab file looks like this:

  GNU nano 2.0.6               File: fstab                                      

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=53a54cbc-abc0-4e15-80d7-ba1af717b97b /               ext3    defaults,erro$
# /dev/sda1
UUID=68F4878CF4875AE8 /media/sda1     ntfs    defaults,umask=007,gid=46 0      $
# /dev/sdb2
UUID=e7a35911-bb84-4b7e-9daa-98ae69b5c2bf none            swap    sw           $
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/sdc1
/dev/sdc1 /media/My Book auto noauto,user,sync 0 0

On reboot though, the usb drive does not mount automatically.  I do notice that in the fstab file all the other drives have UUID information like UUID=68F4878CF4875AE8 /media/sda1.

Help

---

### Post by BuffaloX on 2008-01-27
Some new external drives won't wake up automatically with Linux, because the vendors screwed it up.

Check google for you drive, or at least throw a note on which make and model your drive is.

---

### Post by sonic6567 on 2008-01-27
Mine is an external USB 2 Maxtor One Touch 160G

---

