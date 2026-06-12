---
title: "Hard Drive space is acting weird"
date: 2007-11-18
forum: General Help
---

### Post by TorchlightJay on 2007-11-18
I am running Ubuntu 7.10 and had like 12 Gigs left on space. All of the sudden, it says my hard drive is full. I was using Frostwire at the time I noticed this but I was downloading a music video of about 30 megs so I doubt that did it. I cleared my trashcan. My filesystem is ext3 and I do not understand what could've caused it cause it seemed to happen all of the sudden. I haven't installed much on it lately, and I did just install something and it installed. 

It doesn't make sense, any ideas?

---

### Post by atlfalcons866 on 2007-11-18
how big is your hard drive?

---

### Post by TorchlightJay on 2007-11-18
it's like 120 GIG, the partition i am using is about 25 gigs.

---

### Post by atlfalcons866 on 2007-11-18
i guess the other 12GB is reserved by ext3.

you change it by doing
sudo tune2fs -m 2 /dev/sdax

where x is your partition number

---

### Post by TorchlightJay on 2007-11-18
so what would that do? I am just wanting to make sure. All 120 Gigs are formated. Like 2 is swap, i have two 25 gigs for Ubuntu and SusE, and then the rest is one where I keep my files. (likr 70 gigs). I don't want to ruin the others. The ubuntu and suse are ext3, the storage is reiser. So ya, that storage one i mount to both ubuntu and suse and keep common files there (music, documents, videos, etc.). Again I don't want to harm the others. the SuSE is fine and so is the storage, it's just the ubuntu.

---

### Post by atlfalcons866 on 2007-11-18
that command would reduce the reserved blocks that ext3 reserves.

read man tune2fs for more info 

Post your fdisk by doing
sudo fdisk -l

---

### Post by TorchlightJay on 2007-11-18
```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cfa88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8796    70653838+  83  Linux
/dev/sda2            8797        9019     1791247+  82  Linux swap / Solaris
/dev/sda3            9020       11792    22274122+  83  Linux
/dev/sda4   *       11793       14593    22499032+  83  Linux
```


That's what my fdisk says. I tried that one command and it set it to 2% whatever that means.

---

### Post by atlfalcons866 on 2007-11-18
is the space problem fixed?
Also post df -h

---

### Post by TorchlightJay on 2007-11-18
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda4              22G   12G  8.9G  56% /
udev                  502M   76K  502M   1% /dev
/dev/sda1              68G   62G  5.9G  92% /home/user/Storage
/dev/sda3              21G   21G  360M  99% /mnt/ubuntu

```

no, it hasn't been fixed. I am in my suse partition right now? Thanks.

---

### Post by smartboyathome on 2007-11-18
Well, according to what you just posted, The partition only has 21 MBs, not 25. But it is full, so you may have to delete some stuff. :(

---

### Post by TorchlightJay on 2007-11-18
my bad, thought it was 25, but either way, last time I checked, it said I had lik 8 or 10 gigs left. I haven't done anything strange or any massive downloads to that partition. So it makes no sense why it'd automatically say that it's full. I have nothing really to delete cause I keep everything in the storage partition. Something else might be wrong.

---

### Post by bingoUV on 2007-11-19
You'll have to figure out where the extra stuff is. There is a graphical tool for this (baobab). Don't mind the funny name, it is a reasonably good app. See if it is installed, if not, install it and run it on the folder where you have mounted the partition.

There is a good command line way too.
```

cd /mnt/ubuntu
du -h --max-depth=1

```

This will tell you sizes of all folders. Drill down in suspiciously large folders, and you will reach the culprit soon.

---

