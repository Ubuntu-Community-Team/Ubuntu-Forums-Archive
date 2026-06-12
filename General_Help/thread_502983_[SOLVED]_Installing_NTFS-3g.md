---
title: "[SOLVED] Installing NTFS-3g"
date: 2007-07-17
forum: General Help
---

### Post by Auax on 2007-07-17
Ok, so I've followed the steps on this page: [http://doc.gwos.org/index.php/NTFS-3g](http://doc.gwos.org/index.php/NTFS-3g) got it installed... then I get to the configuration section... I type in ```
sudo fdisk -l | grep NTFS
``` and nothing happens... I just get my prompt.

---

### Post by Outrunner on 2007-07-17
It works for me. maybe you don't have a NTFS partition. Can you post the output of
```

sudo fdisk -l
```

---

### Post by Auax on 2007-07-17
```

/dev/sda1   *           1        1019     8185086   12  Compaq diagnostics
/dev/sda2            1020        7826    54677227+   6  FAT16
/dev/sda3            7827       14200    51199155   83  Linux
/dev/sda4           14201       14593     3156772+  82  Linux swap / Solaris

```
This is very odd... I know that sda2 is an NTFS... it had Vista on it... and I do not own a Compaq.

---

### Post by Outrunner on 2007-07-17
But does it still have Vista on it? If not, after removing Vista, did you format that drive somehow(how, as in what tools, options)? Do you have /dev/sda2 mounted? if not, do this:
```

sudo mkdir /mnt/sda2
```

```
sudo mount /dev/sda2 /mnt/sda2
```

now cd to /mnt/sda2
```

cd /mnt/sda2
```

If it's a NTFS drive, you shouldn't be able to write to it, so try

```
sudo mkdir fat16
```

If it really is partitioned as FAT16 then you should be able to make a directory called 'fat16'. I'm telling you to do this because it might be a wrong reading - so we're testing this theory.

---

### Post by Auax on 2007-07-17
Yes, Vista is still on it, and I didn't modify that partiftion in any way.

How do I know if it's mounted?

---

### Post by Outrunner on 2007-07-17
You can type this in hte terminal:
```
mount
```

if /dev/sda2 is mentioned, then it is mounted(you should see where, as well)

---

### Post by Auax on 2007-07-17
> **Outrunner said:**
> You can type this in hte terminal:
```
mount
```

if /dev/sda2 is mentioned, then it is mounted(you should see where, as well)

```
admin@Hades:~$ mount
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
/dev/sda1 on /media/sda1 type ntfs (rw,nls=utf8,umask=007,gid=46)
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
tmpfs on /lib/modules/2.6.15-26-386/volatile type tmpfs (rw,mode=0755)

```

---

### Post by Outrunner on 2007-07-17
This

```
/dev/sda2            1020        7826    54677227+   6  FAT16
```

and this

```
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
```

don't quite go together... Either fdisk outputted a wrong reading or your /etc/fstab has an outdated entry for /dev/sda2

What happens if you do this?

```
sudo mkdir /media/sda2/fat16/
```

Does it let you?

---

### Post by Auax on 2007-07-17
```
mkdir: cannot create directory `/media/sda2/fat16/': Read-only file system
```

---

### Post by Outrunner on 2007-07-17
> **Auax said:**
> ```
mkdir: cannot create directory `/media/sda2/fat16/': Read-only file system
```

Might as well go on with the guide, because it seems it really is a NTFS partition.

---

### Post by Auax on 2007-07-17
So... what do I do now?

---

### Post by Outrunner on 2007-07-17
It's fairly straight forward :D

You have to make a backup of your /etc/fstab

```
sudo cp /etc/fstab /etc/fstab.bak
```

now edit your fstab

```
gksudo gedit /etc/fstab
```

you should find a line that looks like this:

```
/dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
```

prefix it with a # to make it look like this

```
# /dev/sda2 on /media/sda2 type ntfs (rw,nls=utf8,umask=007,gid=46)
```

Now, below the above line (pun ;) ) copy and paste this

```
/dev/sda2 on /media/sda2 type ntfs-3g defaults,locale=en_US.utf8 0 0
```

Now unmount sda2
```

sudo umount /dev/sda2
```

remount it

```
sudo mount /dev/sda2
```

You should now be able to happily read/write to your NTFS partition - if you still can't, restart your computer. Have fun!

---

### Post by Auax on 2007-07-17
I got this:

```
[mntent]: line 8 in /etc/fstab is bad
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
```

---

### Post by Outrunner on 2007-07-17
What command outputs this? 

Also, post the output of ```
cat /etc/fstab
``` and I can fix it for you ;)

---

### Post by Auax on 2007-07-17
> **Outrunner said:**
> What command outputs this? 

Also, post the output of ```
cat /etc/fstab
``` and I can fix it for you ;)

It was the mount command that made that one.

```
admin@Hades:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
# /dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46
/dev/sda2 on /media/sda2 type ntfs-3g defaults,locale=en_US.utf8 0 0
0       1
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by Outrunner on 2007-07-17
Ahh yes, you see, the 8th line should look like this
```

/dev/sda2 on /media/sda2 type ntfs-3g defaults,locale=en_US.utf8 0 0 0       1
```

as far as I can tell. However, you split it into two lines, making it look like this

```
/dev/sda2 on /media/sda2 type ntfs-3g defaults,locale=en_US.utf8 0 0
0       1
```

So the 8th line is "bad", to put it like that, because it is incomplete.

just open your /etc/fstab

```
gksudo gedit /etc/fstab
```

And make sure the file looks like this, and exactly like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0    1
# /dev/sda2       /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46
/dev/sda2 /media/sda2        ntfs-3g defaults,locale=en_US.utf8 0 0 0       1
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Just copy and paste the contents over your current one.

---

### Post by Auax on 2007-07-17
I still get the same error when I try to mount sda2

---

### Post by Outrunner on 2007-07-17
You know, I just looked over the 8th line again. There were a few extra words like 'on' included, and I have no idea why *sigh* 

So, once again open your /etc/fstab file and replace the 8th line with

```
/dev/sda2 /media/sda2        ntfs-3g defaults,locale=en_US.utf8 0 0 0       1
```

I really don't see any extra words there this time. Jeez, how did they get there anyway? :confused:

---

### Post by Auax on 2007-07-17
Ok, I have this:
```
admin@Hades:~$ sudo mount /dev/sda2
WARNING: Deficient Linux kernel detected. Some driver features are
         not available (swap file on NTFS, boot from NTFS by LILO), and
         unmount is not safe unless it's made sure the ntfs-3g process
         naturally terminates after calling 'umount'. If you wish this
         message to disappear then you should upgrade to at least kernel
         version 2.6.20, or request help from your distribution to fix
         the kernel problem. The below documentation has more information:
         /usr/share/doc/ntfs-3g/README.Debian

```

And thank you very much for all your help. =]

---

### Post by Outrunner on 2007-07-17
No problem, although, I have to admit it took me an unnecessarily long time to find the problem. Guess I should be more attentive :oops:

---

### Post by Auax on 2007-07-17
Well, you're working with a complete Linux newb here too. =D

---

