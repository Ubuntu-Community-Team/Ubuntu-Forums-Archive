---
title: "media folder problem"
date: 2008-07-04
forum: General Help
---

### Post by kboy on 2008-07-04
Hi,
 i've recently noticed that my my "File System" partition is getting full without installing any new software or adding anything to that partition.
but i was adding music and movies to my other ntfs partitions (they are automatically mounted at boot).
and now the entire "file system" free space is 10 kb!!!

is it supposed to be this way??? I mean i have only 30 GB of space in the "file system" partition and most of the size is taken by the media directory.

---

### Post by iaculallad on 2008-07-04
> **kboy said:**
> Hi,
 i've recently noticed that my my "File System" partition is getting full without installing any new software or adding anything to that partition.
but i was adding music and movies to my other ntfs partitions (they are automatically mounted at boot).
and now the entire "file system" free space is 10 kb!!!

is it supposed to be this way??? I mean i have only 30 GB of space in the "file system" partition and most of the size is taken by the media directory.

Try to remove installed software caches in your system.

```
sudo apt-get clean
```

Or try removing OLD installed kernels using Synaptics.

Try to post whatever displays when you issue this terminal command:

```
df -h
```

---

### Post by cariboo on 2008-07-04
You probably have been doing updates and you might have an extra kernel or two. In a terminal type:

```
sudo apt-get clean
```

This will clean out all the archived files from all the updates, and other programs you have  installed.

Also check to see how many kernels you are keeping around. The quick way is to count the number of kernels you see in the grub boot menu. Note which kernels you have and then search for then using synaptic. You should only have two, the current and previous kernels. get rid of any others.

Edit: I guess I took to long


Jim

---

### Post by kboy on 2008-07-04
the output of "df -h" is:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              25G   23G  744M  97% /
varrun                252M  200K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   76K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             7.9G  2.3G  5.6G  30% /media/sda1
/dev/sda2              39G  4.3G   35G  11% /media/sda2
/dev/sda3              39G  3.5G   36G   9% /media/sda3
```

the used space of sda1+sda2+sda3 takes this space from the sda5 (my root filesystem) in addition to space they take in their own partitions.

---

### Post by iaculallad on 2008-07-04
> **kboy said:**
> the output of "df -h" is:

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              25G   23G  744M  97% /
varrun                252M  200K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
udev                  252M   76K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   34M  218M  14% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             7.9G  2.3G  5.6G  30% /media/sda1
/dev/sda2              39G  4.3G   35G  11% /media/sda2
/dev/sda3              39G  3.5G   36G   9% /media/sda3
```

the used space of sda1+sda2+sda3 takes this space from the sda5 (my root filesystem) in addition to space they take in their own partitions.

Well then, its time to give your system a disk clean-up by following the instructions on my first post.

And addition on deleting OLD kernels using Synaptics, on the "Search Option", input the string "linux-image" (w/o double quote) to search for your kernel files. Right click on the OLD kernels you want to delete and select "Mark for Complete Removal" and click "Apply". Do leave (1) OLD kernel just in case.

---

### Post by kboy on 2008-07-04
i have only two kernels installed the 14 and 15. i guess the 14 is the old one. should i remove it???

---

### Post by iaculallad on 2008-07-04
> **kboy said:**
> i have only two kernels installed the 14 and 15. i guess the 14 is the old one. should i remove it???

If you're not experiencing any OS glitches when you installed your NEW kernel, then, it would be safe to remove it.

Don't forget the:

```
sudo apt-get clean
```

terminal command.

---

### Post by kboy on 2008-07-04
i did it all!!! nothing helps!!!
there 10 GB of used space in the root file system that don't belong their, they are the data that is stored in the ntfs partitions.

sorry for being such a pain....

---

### Post by iaculallad on 2008-07-04
> **kboy said:**
> i did it all!!! nothing helps!!!
there 10 GB of used space in the root file system that don't belong their, they are the data that is stored in the ntfs partitions.

sorry for being such a pain....

How come they are in your / filesystem instead on your other ntfs partition? You could try to cut-and-paste it back to your other partition if you know where those file are located:

On your terminal, issue the command below to give you privilege to cut-and-paste.

```
gksudo nautilus
```

---

### Post by kboy on 2008-07-04
I don't know exactly what to tell you, all I know is that my ntfs partitions are mounted in the media folder of the root file system.
and that media folder takes the same size as my ntfs partitions.

i can't delete anything from the media folder because it will be removed from the partitions.

---

### Post by iaculallad on 2008-07-04
Yes, disk content and content size of your NTFS partition should equal that of the folder fount in your /media directory because it serves as your mount point and actually, it's not taking any space on your filesystem. It's just a mirror that you're seeing.

*It's not actually taking spaces in your / partition*

EDIT: To better understand, try reading this [page]("http://www.tuxfiles.org/linuxhelp/mounting.html").

---

### Post by kboy on 2008-07-04
thanks!!!

I found out what was taking so much space!
it wasn't the media folder, it's the /var/log folder that takes a size of 15 GB!!!
anyone have an idea why???

---

