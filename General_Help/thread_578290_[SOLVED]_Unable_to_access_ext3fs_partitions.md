---
title: "[SOLVED] Unable to access ext3fs partitions"
date: 2007-10-17
forum: General Help
---

### Post by ithaka on 2007-10-17
Hi all,


In the progress of moving from WinXP to Ubuntu (7.04 for the moment, and counting down...) I have converted my NTFS partitions to ext3fs using gparted.

The conversion went successful and the partitions are recognized correctly however, I have no access to the partitions unless I enter the root password and even then I can't do anything on the partition (only read access it seems).

Now I thought I had to add them to fstab, but all the documentation I found was only talking about adding Windows partitions to the config file. Should I do this with the Linux partitions too? And how?


Thanks!

---

### Post by questpro on 2007-10-17
Please provide some more information.

1. post the /etc/fstab

2.a screenshot of gparted showing your partitions

---

### Post by ithaka on 2007-10-17
Hi,


As requested my fstab and a screenshot from gparted. For the record, I did not change anything on the fstab. All values in there are coming from the system.

How did it grow like this? Under Windows I had:
 - a partition containing Windows
 - a partition containing all the applications
 - 2 more partitions containing all my and a backup of my spouse's documents and 'stuff' ;-)

To install LInux I made the 2 partitions and the extended partition smaller and added the single ext3fs root partition at the end.

I also can't make one partition of the two ext3fs partitions in the extended because gparted seems to mount them automatically and comes complaining I have to ' unmount all logical partitions with a number higher then 7'.

While talking on the partition stuff, about 10 year ago I did my first steps in Linux (Redhat 3.0) and the mounting / unmounting aspect was clearer to me back then. Currently there is also something like the media folder of which the functionality is not quite clear. I think it has to do with the drive icons that come and go on my desktop, but I do not get a grip on it (I want them all gone by the way). Some good article on that is always welcome too, I do not seems to find any.


Thanks for the help.

---

### Post by questpro on 2007-10-18
> **ithaka said:**
> Hi,

How did it grow like this? Under Windows I had:
 - a partition containing Windows
 - a partition containing all the applications
 - 2 more partitions containing all my and a backup of my spouse's documents and 'stuff' ;-)

To install LInux I made the 2 partitions and the extended partition smaller and added the single ext3fs root partition at the end.

I also can't make one partition of the two ext3fs partitions in the extended because gparted seems to mount them automatically and comes complaining I have to ' unmount all logical partitions with a number higher then 7'.

While talking on the partition stuff, about 10 year ago I did my first steps in Linux (Redhat 3.0) and the mounting / unmounting aspect was clearer to me back then. Currently there is also something like the media folder of which the functionality is not quite clear. I think it has to do with the drive icons that come and go on my desktop, but I do not get a grip on it (I want them all gone by the way). Some good article on that is always welcome too, I do not seems to find any.


Thanks for the help.

Apparently, you have to alter your /etc/fstab . If you are upgrading to 7.10 , it will fix it by asking you.   

/media directory is the place where your windows partitions are mounted. You can mount in any other place as well by changing /etc/fstab file. But those partitions are not displayed on the desktop.

Lately I have done some stuff like this. So I could only suggest. I am not an expert.

_Modifying your /etc/fstab :_ 
At first please make a back up copy of /etc/fstab

There is no entry of your ext3fs partition you made. So you can add that entry the same way the other ext3 partition is. 

And you can modify the windows partitions accordingly. Its pretty simple. Because there are all mounted in the /media folder, you can cross check with the /etc/fstab file. And modify accordingly. Just ignore the UUIDs and replace with /dev/...(whatever your drive name)

Then unmount the partitions and mount them again in the terminal using the commands: 

sudo umount -a
sudo mount -a

Let me know if there are any problems...

---

### Post by questpro on 2007-10-18
Do you have hd1,hda5,hda6 in /media

Because I can not see them in your gpated screenshot...That means there are not mounted at that place.

---

### Post by ithaka on 2007-10-21
Indeed,

This is the content of the media folder

----------------------------
[FONT="Verdana"]lrwxrwxrwx 1 root root       6 2007-08-27 23:29 cdrom -> cdrom0
drwxr-xr-x 2 root root    4096 2007-08-27 23:29 cdrom0
drwxrwx--- 1 root plugdev 4096 2007-09-27 18:22 hda1
drwxrwx--- 1 root plugdev 4096 2007-09-27 19:59 hda5
drwxr-xr-x 2 root root    4096 2007-08-27 23:29 hda6
drwxr-xr-x 2 root root    4096 2007-08-27 23:29 hda7[/FONT]
----------------------------

---

### Post by bodhi.zazen on 2007-10-21
See if this helps :

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by ithaka on 2007-10-31
Thanks! The link with the HOWTO cleared up a lot on the fstab file and I have got it now like I wanted.

---

