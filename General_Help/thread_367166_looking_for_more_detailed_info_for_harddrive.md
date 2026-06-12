---
title: "looking for more detailed info for harddrive"
date: 2007-02-21
forum: General Help
---

### Post by talon 2 on 2007-02-21
Hi everyone,

           I  know this is should be easy. I can se the size of my harddrive, but was looking to find out what remaining space is available. I tried different things with no luck.:)

---

### Post by Strider on 2007-02-21
When you safe the hard drive are you using the whole HD for your OS?  You can use "df" (do a "man df" to find out how to use it).  Normally run "df -h" will show you all mounted partitions with actual size, used, and available.

-Mike

---

### Post by talon 2 on 2007-02-21
Hi mike,
   I am new to linux.  I tried to open the terminal and type in some of the text. I was getting command not found. I have to admit this is my first attempt at using the terminal . So this is new for me. I will keep trying any more info would be great.

---

### Post by Maestro23 on 2007-02-21
Open terminal, and type:

> df -l (lower case L)



To see other uses of "df", type:

> man df

---

### Post by talon 2 on 2007-02-21
To answer your question from before my harddrive is partioned in half with windows on the other part of the harddrive.

---

### Post by talon 2 on 2007-02-21
Thanks maesro 23,
        The  df-l did not work.  typed in man df which brought up text.  then treid just df and did get some break down on my harddrive.

---

### Post by yabbadabbadont on 2007-02-21
df -h

Will give you the information in "human readable" format.  Example:
```
/home/bubba $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda7              12G  2.4G  8.2G  23% /
varrun                379M   72K  379M   1% /var/run
varlock               379M  8.0K  379M   1% /var/lock
udev                  379M  176K  379M   1% /dev
devshm                379M     0  379M   0% /dev/shm
lrm                   379M   18M  361M   5% /lib/modules/2.6.15-28-k7/volatile
/dev/hda5             236M   14M  210M   7% /boot
/dev/hda8              30G  324M   30G   2% /home
/dev/sda5              32G  8.7G   22G  29% /media/backup
/dev/sda6              63G   27G   35G  44% /media/music
/dev/sda8              63G   60G  3.5G  95% /media/vids1
/dev/sda9              61G   56G  4.9G  93% /media/vids2
/dev/sda7              12G  7.2G  4.7G  61% /media/walls
/dev/hda1              32G   18G   15G  54% /media/win

```

---

### Post by Maestro23 on 2007-02-21
> **talon 2 said:**
> Thanks maesro 23,
        The  df-l did not work.  typed in man df which brought up text.  then treid just df and did get some break down on my harddrive.

df (space) -l

df -h

---

