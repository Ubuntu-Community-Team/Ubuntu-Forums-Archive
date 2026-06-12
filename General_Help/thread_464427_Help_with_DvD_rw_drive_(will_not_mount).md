---
title: "Help with DvD rw drive (will not mount)"
date: 2007-06-04
forum: General Help
---

### Post by kdarkentity on 2007-06-04
my dvd drive on my laptop will not mount for some random reason

---

### Post by jimbob on 2007-06-04
Under System->Preferences->Removable . Drives &Media->Removable Storage which boxes do you have checked?

Can you mount it manually?&#65279;
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by kdarkentity on 2007-06-04
in system preferences removable drives i have the following settings checked

mount emovable drives when hot plugged

mount removble media when inserted

browse removable storage when inserted

---

### Post by jimbob on 2007-06-05
See that under System->Preferences->Removable . Drives &Media->Multimedia you also have Play Video DVD Discs checked.

Post a copy of your /etc/fstab.

Try to mount the DVD manually with this command:
  
   sudo mount -t iso9660 /dev/hdd /media/cdrom1

(look in /etc/fstab to find out if your drive is hdc or hdd and if the mount point is cdrom0 or cdrom1 and modify the command accordingly).
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by kdarkentity on 2007-06-05
well i dont have permission to see etc/fstab soo i used the command sudo mount and this is what i got...



sudo mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

i  also tried the commands you told me to try and they were unsuccessful

---

### Post by jimbob on 2007-06-05
Any user can view /etc/fstab  - it has worldwide read permissions.  

Enter [COLOR="Blue"]cat /etc/fstab[/COLOR] in a terminal window and paste the output in your reply.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by kdarkentity on 2007-06-06
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b89a0f1d-a640-4338-a098-a26c6c460c56 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=70a38477-5993-47d9-9e6e-c78e1b9ad03d none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by jimbob on 2007-06-06
OK, at least your system sees the drive as /dev/scd0.

Put a dvd in the drive and see if you can mount it manually by entering this command from a terminal window:

  sudo mount -t iso9660 /dev/scd0 /media/cdrom0
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by kdarkentity on 2007-06-06
i tried that and i get this error

mount: special device /dev/sdc0 does not exist

---

### Post by DagMan on 2007-06-06
/dev/scd0 or /dev/sdc0
was the mistype here or in the terminal.

also, please post the output of
```
ls -l /dev/cd* /dev/dv*
```

---

### Post by kdarkentity on 2007-06-06
here are the results for...

ls -l /dev/cd* /dev/dv*


lrwxrwxrwx 1 root root 3 2007-06-06 10:16 /dev/cdrom -> hda
lrwxrwxrwx 1 root root 3 2007-06-06 10:16 /dev/cdrw -> hda
lrwxrwxrwx 1 root root 3 2007-06-06 10:16 /dev/dvd -> hda
lrwxrwxrwx 1 root root 3 2007-06-06 10:16 /dev/dvdrw -> hda

---

### Post by DeathStar on 2007-06-06
Hi,

Not sure if it's the same issue, but I had a problem with DVD's not mounting.

[[COLOR="Blue"]TRY THIS[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2794119#post2794119")

DS

---

