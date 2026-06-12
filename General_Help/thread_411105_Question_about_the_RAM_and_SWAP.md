---
title: "Question about the RAM and SWAP"
date: 2007-04-16
forum: General Help
---

### Post by RedMaster on 2007-04-16
Hi!
Amm I want to ask you why my linux dont use the swap memory... It uses only the ram memory... Is it normal to use more than 800MB from 1GB of RAM ? Yeah i know that KDE uses a lot of memory, but... :| 

Im using Ubuntu 6.06 and KDE 3.5.2 :)

Sorry for the noob question, but im newbie :|

Thank you alot :)

---

### Post by phidia on 2007-04-16
What does the command > free output?

Also check out this thread [http://www.techspot.com/vb/all/windows/t-7549-Linux-Swap-partition.html](http://www.techspot.com/vb/all/windows/t-7549-Linux-Swap-partition.html)

---

### Post by RedMaster on 2007-04-16
> **phidia said:**
> What does the command  output?

Also check out this thread [http://www.techspot.com/vb/all/windows/t-7549-Linux-Swap-partition.html](http://www.techspot.com/vb/all/windows/t-7549-Linux-Swap-partition.html)

Hmm, from that thread i have understand that maybe i didnt format the SWAP partition when i installed tha ubuntu... and also that maybe it is not mentioned in the /etc/fstab... but i dont know how to mention it there :| 

Can you help me? :)

---

### Post by MRiGnS on 2007-04-16
Linux RAM-management works kind of different from the Windows one. Linux uses the RAM to cache things to increase the stability and performance. Swap comes in when you install large things, with apt-get for example, or when you work on pictures and movies.

The swap should be at least as big as the RAM to allow the hibernate mode.
Most say it should be twice as big as you RAM.

so 1GB ram would result in 2GB swap.

---

### Post by RedMaster on 2007-04-16
> **MRiGnS said:**
> Linux RAM-management works kind of different from the Windows one. Linux uses the RAM to cache things to increase the stability and performance. Swap comes in when you install large things, with apt-get for example, or when you work on pictures and movies.

The swap should be at least as big as the RAM to allow the hibernate mode.
Most say it should be twice as big as you RAM.

so 1GB ram would result in 2GB swap.

Yep, I know that, but I think that maybe swap file is not switched on :| here is what "free" gave me back:

```
redmaster@redmaster-desktop:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
/dev/sda7 / ext3 nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
/dev/sda1 /media/sda1 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/sda5 /media/sda5 ntfs defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser 0 1
/dev/sda6 none swap sw 0 0
/dev/hdb /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda3 /media/hdd vfat noauto,uid=0,gid=0,rw,nouser 0 0

```

---

### Post by phidia on 2007-04-16
In a common install swap is usually set up for you if you selected to manually partition you would need to chose a swap partition. 
~$ free
             total       used       free     shared    buffers     cached
Mem:        516016     508816       7200          0      71784     189352
-/+ buffers/cache:     247680     268336
Swap:      1959848          0    1959848

The above is what "free" outputs on my computer and the fstab for swap is 
# /dev/hda5
UUID=72835d4c-2c8b-4f55-bdb6-5861517aadf1 none            swap    sw              0       0
# /dev/sda5
UUID=232a0d4d-505b-47cc-81aa-2d3f0a0a66d8 none            swap    sw              0       0

take a look at the manpage for mkswap i.e. > man mkswap

---

