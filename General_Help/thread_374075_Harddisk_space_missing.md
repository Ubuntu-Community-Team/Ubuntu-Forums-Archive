---
title: "Harddisk space missing"
date: 2007-03-02
forum: General Help
---

### Post by narx on 2007-03-02
Hi Guys and girls,

Been using ubuntu for a couple of months and i love it. Any problem that i came across could be easily solved by just browsing through this helpful forum..

But unfortunately, i couldnt find the solution to this problem i've been facing..

I'm wondering what happen to my hard disk space. (approx 300MB+-) has gone missing..

here is df out put

Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             7.0G  6.0G  657M  91% /
proc                     0     0     0   -  /proc
/sys                     0     0     0   -  /sys
varrun                375M   88K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
procbususb             10M  148K  9.9M   2% /proc/bus/usb
udev                   10M  148K  9.9M   2% /dev
devshm                375M     0  375M   0% /dev/shm
devpts                   0     0     0   -  /dev/pts
/dev/hda1              25G   17G  8.1G  68% /media/hda1
/dev/hda2             4.6G  4.0G  585M  88% /media/hda2
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
tmpfs                 375M   18M  358M   5% /lib/modules/2.6.17-11-generic/volatile

Could it be because  " tmpfs " has consumed it? If so , how do i realease thoese valuable harddisk space of mine.

Thanks guys and girls.!!

Best regards,
clayton

---

### Post by narx on 2007-03-03
bump

---

### Post by taurus on 2007-03-03
Have you looked in your trash directory to make sure you actually delete those files?

```
ls -la ~/.Trash
```
Also, you need to empty your cache with

```
sudo aptitude clean
```
Then, may want to check /var to make sure there is nothing big in there.

```
sudo du -h /var
```

---

### Post by narx on 2007-03-09
yup did all those..

but yet it's still a mystery to me..

---

### Post by narx on 2007-03-12
bump

---

### Post by mcduck on 2007-03-12
5% of disk space on Ext3 file system is reserved for root user only, to make sure that root can always access computer and normal users can't fill the disk to 100%. This space isn't even visible when you check the disk sizes as normal user. Since you didn't tell which of your disks is missing the space, or how you came to conclusion that some space is missing, I would bet that the 5% thing is what your problem is.

---

### Post by narx on 2007-03-15
Thanks man....

that would make sense

---

