---
title: "Resizing Ubuntu Partition"
date: 2008-06-21
forum: General Help
---

### Post by RATM_Owns on 2008-06-21
I'm going to resize my Ubuntu partition a little bit so I have somewhere to put another linux distribution. 

I was wondering if resizing it might do something bad to the filesystem or not.

---

### Post by avtolle on 2008-06-21
Well, as you know the first rule is to backup all your important files and data to external media before beginning the resize. I've resized "up and down" in the past without issue, but that means nothing for the next time for me, or for you at present.

Standard stuff: I'm sure you know you will need to do this from a Live CD, as a mounted partition cannot be worked on, so use either your Ubuntu Live CD, or get a bootable live cd from Gparted website, or a bootable Live CD of your favorite partitioner. Go slowly, be careful, and good luck.

---

### Post by geirha on 2008-06-21
The procedure is quite well tested, and your filesystem will not be harmed. However, consider something unexpected happens. Say your computer loses power in the middle of the procedure. I'm sure you can imagine that that's a bad thing, and that you may lose data. That's why you would want to back up important data.

---

### Post by AmonSacha on 2008-06-21
Gparted live cd is great for such things.

Here is the link to the liveCD page: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

also it may be easier if you have a second operating system it may be easier to unmount the ubuntu volume and resize it from that.

---

### Post by lswb on 2008-06-21
I've resized partitions several times and never had an issue, but even so, I always make a backup first.

---

### Post by tad1073 on 2008-06-21
The only problem I have found is when you resize your swap partition, the uuid # changes and swap will not mount at boot. With 7.10 you could look under devices, or something to that effect, find the new uuid # then edit fstab to reflect the new uuid #.

With 8.04 however, I can not find the uuid # of the new swap partition.

---

### Post by itix on 2008-06-21
Gparted Live CD worked wonders for me. That's more than one can say about the Open SUSE that I installed.

...oh and one more thing, RATM is overrated ;)

---

### Post by geirha on 2008-06-21
> **tad1073 said:**
> The only problem I have found is when you resize your swap partition, the uuid # changes and swap will not mount at boot. With 7.10 you could look under devices, or something to that effect, find the new uuid # then edit fstab to reflect the new uuid #.

With 8.04 however, I can not find the uuid # of the new swap partition.

Running either of the following commands in a terminal
```

sudo blkid
ls -l /dev/disk/by-uuid

``` should show the UUID in all the currently supported ubuntu releases.

---

### Post by tad1073 on 2008-06-21
> **geirha said:**
> Running either of the following commands in a terminal
```

sudo blkid
ls -l /dev/disk/by-uuid

``` should show the UUID in all the currently supported ubuntu releases.

Thanks for the info it help tremendously.

---

