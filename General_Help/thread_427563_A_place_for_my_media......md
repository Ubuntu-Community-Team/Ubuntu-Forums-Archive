---
title: "A place for my media....."
date: 2007-04-29
forum: General Help
---

### Post by MrGreen on 2007-04-29
Hi,

I am currently storing all my media [Music Photos etc... ] on /media on a separate hard drive.. 

Would it be better to keep it in /home freeing up my second drive either for dual booting or for raid

```

 [ ~ ] > df -hT
Filesystem Type    Size Used Avail Use% Mounted on
/dev/sda3     ext3     19G  2.9G   15G  16% /
varrun       tmpfs   1014M  100K 1014M   1% /var/run
varlock      tmpfs   1014M     0 1014M   0% /var/lock
procbususb   usbfs   1014M  144K 1014M   1% /proc/bus/usb
udev         tmpfs   1014M  144K 1014M   1% /dev
devshm       tmpfs   1014M     0 1014M   0% /dev/shm
lrm          tmpfs   1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1     ext3     92M   16M   72M  18% /boot
/dev/sda4     ext3    206G  6.4G  189G   4% /home
/dev/sdb3     ext3    229G   27G  192G  13% /media
```

---

### Post by dcstar on 2007-04-30
> **MrGreen said:**
> Hi,

I am currently storing all my media [Music Photos etc... ] on /media on a separate hard drive.. 

Would it be better to keep it in /home freeing up my second drive either for dual booting or for raid

```

 [ ~ ] > df -hT
Filesystem Type    Size **Used Avail Use%** Mounted on
/dev/sda3     ext3     19G  2.9G   15G  16% /
varrun       tmpfs   1014M  100K 1014M   1% /var/run
varlock      tmpfs   1014M     0 1014M   0% /var/lock
procbususb   usbfs   1014M  144K 1014M   1% /proc/bus/usb
udev         tmpfs   1014M  144K 1014M   1% /dev
devshm       tmpfs   1014M     0 1014M   0% /dev/shm
lrm          tmpfs   1014M   33M  981M   4% /lib/modules/2.6.20-15-generic/volatile
/dev/sda1     ext3     92M   16M   72M  18% /boot
/dev/sda4     ext3    206G  **6.4G**  189G   4% /home
/dev/sdb3     ext3    229G   27G  **192G  13% /media**
```

How do you expect to put 192G of data onto a partition with only 6.4G free?

---

### Post by Nythain on 2007-04-30
i think thats only 6.4 used, with 189 free... and yeah, you could just use your /home for storing stuff... thats kinda what it was originally designed for and all... since its its own partition that makes it even better, so you dont lose the info if you ever have to reinstall... and it can be mounted inside other distro's and or os's also... should work great if you really want to reserve that second drive for dual boot/ raid

---

### Post by MrGreen on 2007-04-30
Yeah I'm thinking it may be better to put my sounds in /home always backup ... /media thinking now about testing 64 version see if it works ok 

Raid might get messy because I have never used it not sure I would see any real gain

Thanks guys...

---

### Post by strabes on 2007-04-30
Keep your data separate. It's safer that way. If it ain't broke, don't fix it. You could do some shrinking of partitions to dual boot if you wanted to.

---

