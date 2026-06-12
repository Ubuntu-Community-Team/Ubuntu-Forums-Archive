---
title: "/root Disk Usage is Red!"
date: 2006-12-06
forum: General Help
---

### Post by nubie777 on 2006-12-06
Life is full of surprises!  I installed ubuntu server on a 36GB partition (ext3) and another 1GB for swap. I next installed GNOME desktop so I could use a GUI to configure.  I installed no other application software; however, two online updates were applied.  I ran Disk Usage Analyzer and to my surprise I found the following:

1.  /     3.2 GB 100%  19 objects; color is [COLOR="Red"]RED[/COLOR]
2.  /usr  1.8 GB  55%  10 objects; color is [COLOR="Yellow"]Yellow[/COLOR]


Can anyone tell me why my root directory is full?  Is there a predefined allocation of disk space to the directories (e.g. /usr, /var, etc...) during the install process?

What can I do to allocate more space to "/" and "/usr"?  Do I need to reinstall and setup a separate partition for "/", "/usr" and any other partition believe will be large?

Thanks a lot for any help!

---

### Post by taurus on 2006-12-06
What's the output of this command from a terminal?

```
df -h
```

---

### Post by CatKiller on 2006-12-06
I don't think that the colouring is to do with allocation - I think it's to do with proportions used. / gets full usage, since everything in the filesystem is in / (by definition). You've still only used 3.2 GiB of your 36 GiB partition, though.

---

### Post by nubie777 on 2006-12-06
Here is: df -h

root@ubuntuServer:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3              36G  2.6G   32G   8% /
varrun                506M   88K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  172K  9.9M   2% /proc/bus/usb
udev                   10M  172K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.17-10-386/volatile
/dev/hdc              452M  452M     0 100% /media/cdrom0

---

### Post by taurus on 2006-12-06
Looks like / only uses 8%, 2.6GB, of space available to it!  What about

```
sudo fdisk -l
cat /etc/fstab
```

---

### Post by nubie777 on 2006-12-06
I've attached two images of the output of the commands.

---

### Post by nubie777 on 2006-12-06
There are 3 disk drives.  win/xp, SuSe and Ubuntu are on the first disk.
For Ubuntu:
/root is hda3 (primary partition) and
swap is hda9 (logical partition)

fyi

---

### Post by CatKiller on 2006-12-06
Really, you aren't mysteriously using lots of space. You're just misinterpreting the information. You might find the [baobab documentation]("http://www.marzocca.net/linux/baobab.html#treemap") useful, or the screenshot in the [anouncement thread]("http://www.ubuntuforums.org/showthread.php?t=45659") useful.

---

### Post by nubie777 on 2006-12-06
Here is a graphical view of the disk:

---

### Post by taurus on 2006-12-06
Just an observation.  Why do you have three swap partitions?  I assume you know you can share the same swap partition for both Ubuntu & SUSE.  And since you have three, why not mount them all so you would have a larger swap size!

---

### Post by nubie777 on 2006-12-06
Here is the disk setup:
1. Free space at beginning - use to be PQBoot  - not now.
2. hda1 win/xp
3. extended partition
4. SUSE - hda5
5, SUSE - hda6
6. SUSE - hda7
7. SUSE - swap hda8
8. Ubuntu - swap hda9
9  Ubuntu - primary-hda3-ubuntu made it primary and not logical  

Every day is brings a new learning experience!
Thanks.

---

