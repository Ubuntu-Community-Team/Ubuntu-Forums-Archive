---
title: "NTFS Partition incorrectly showing as full"
date: 2007-12-24
forum: General Help
---

### Post by Shrynn on 2007-12-24
Hey guys I did some searching on this issue and couldn't find much.

I have a NTFS partition mounted under Ubuntu 7.10, this partition was part of my windows installation. Anyway this partition is used to for downloading. 

What's happening is I am suddenly unable to create anymore files because I get a message stating that the device is full. I ran a 'df -k' and here is the output.

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb3             20161172   4821752  14315280  26% /
varrun                  517660       204    517456   1% /var/run
varlock                 517660         0    517660   0% /var/lock
udev                    517660        92    517568   1% /dev
devshm                  517660         0    517660   0% /dev/shm
lrm                     517660     34696    482964   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             78140128  48720992  29419136  63% /media/sda1
/dev/sdb1            134215008 124571216   9643792  93% /media/sdb1
/dev/sdb2             83184568  83137820     46748 100% /media/sdb2

```

/media/sdb2 is the culprit. I've gone in and deleted 10 or 15 gigs off of this drive but it always reads as full..... Odd. I've never had anything like this happen before. Anyone know where to start trouble shooting?

---

### Post by taurus on 2007-12-24
How did you delete files from /media/sdb2?  You probably need to empty your trash bin too.

---

### Post by Shrynn on 2007-12-24
I selected the files, right clicked, Move to Trash.  I have emptied the trash bin with no change. I just tried deleting from the terminal with odd results.

```
/dev/sdb2             83184568  82424500    760068 100% /media/sdb2
```

760 megs free but still 100%....

---

### Post by Jabus on 2008-01-03
I've been googling all day to solve this problem and this is what I've come up with.

```
sudo nautilus /media/sda2/.Trash-username
```

basically for each mount or partition there seems to be a seperate Trash folder. I deleted over 40 gigs off my storage partition but for some reason it kept reporting my drive as fully used up. If the above code doesn't work you may have to select View --> Show hidden files   inside of nautilus. Once you get into your .Trash folder highlight all of it and delete it. Tada.

---

