---
title: "Copying speeds getting slower and slower and then stopping?"
date: 2013-06-20
forum: General Help
---

### Post by hans12345 on 2013-06-20
I am trying to copy (actually a simple minded backup) 48 GB of picture files (20.000 files, typical size 4 MB) from a NAS file server to a USB external drive.

The original process was NAS -> ethernet -> PC -> USB drive

The transfer started quickly enough at 2.5 MBPS (as reported by the copy window of Nautilus) but rapidly slowed right down and eventually stopped after around 12 hours with about 6 GB transferred.

So I decided to make the copy simpler, and just copy to a normal ext4 partition on the PC.

Now I do :  NAS -> ethernet -> PC

It started quickly, at 11.5 MBPS, but again the speed dropped quickly and stopped after about 90 mins with 4800 files of the 20.000 transferred.

The system monitor shows no obvious problem. I suspected some RAM or swap file problem but all looked good.

I'm running 12.10 on a homemade PC, AMD X3 cpu and 4GB RAM.

Any ideas what is going wrong? Where should I be looking?

Thanks.

BTW, this post is similar to "Copying speeds way too slow?", but sufficiently different.

[http://ubuntuforums.org/showthread.php?t=2113958](http://ubuntuforums.org/showthread.php?t=2113958)

---

### Post by ajgreeny on 2013-06-20
Try **rsync** to see if it is a problem of some sort with the command you're using.

I use rsync for my backups from hard drive to an external hard drive and it runs at around 11MB/sec average, admittedly wired, so that may be relevant.

---

### Post by JRV on 2013-06-20
run top:
```

sudo top

```
if a program called gvfs(d)-metadata or something like that (It's been a long time) is taking up a lot of resources run the following:
```

rm -rf /home/jack/.local/share/gvfs-metadata
pkill gvfsd-metadata 

```

---

### Post by hans12345 on 2013-06-21
I think I was fooled by a cache on the drive, or by RAM buffering.

I now think it's mainly a slow USB drive. I did the copy again. It took about 16 hours but went through.

Thanks ajgreeny, I try rsync next time.

Thanks JRV for the tip. I didnt see anything strange with gvfs.

---

