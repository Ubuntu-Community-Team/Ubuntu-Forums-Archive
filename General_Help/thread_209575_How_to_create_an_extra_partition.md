---
title: "How to create an extra partition"
date: 2006-07-05
forum: General Help
---

### Post by ahaslam on 2006-07-05
Hi,

I have Ubuntu as the sole OS on my system, using the entire hard disk.
I have used about 20 of the available 40 Gigs and would like to create a 5-10 Gig partition to test the upcoming development releases and maybe give other OS's a spin. 

Would it be possible to do this *without* destroying my existing data? If so what do I need to use/install - gparted perhaps?

Thank you,

Tony.

---

### Post by hankarun on 2006-07-05
There is some small distros like hiren' s boot cd. There is utulities like partition magic. You can create or delete partitions without data loosing. But are they legal i don' t know

---

### Post by ahaslam on 2006-07-05
[QUOTE=hankarun]There is some small distros like hiren' s boot cd. There is utulities like partition magic. You can create or delete partitions without data loosing. But are they legal i don' t know[/QUOTE]
Thanks for your reply,

Hiren's a **Dos** Bootable CD, I doubt it'll support Linux file systems. Same goes for Partition Magic and I don't think it's free.

Tony.

---

### Post by zhoux on 2006-07-05
gparted has a livecd version....you could try that...though i've never used it before...so....

here's the link: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

---

### Post by ahaslam on 2006-07-05
[QUOTE=zhoux]gparted has a livecd version....you could try that...though i've never used it before...so....

here's the link: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)[/QUOTE]
Yes, it looks good. I am looking at that now. 

Their site says, "The purpose of GParted is to allow the individual to take a hard disk and change the partition organization therein, while preserving the partition contents." - Just what I need!


Thank you,

Tony.

---

### Post by ahaslam on 2006-07-05
Success! :) 

It's done. 

I now have a 30GB root partition, a 896MB Swap partition and 6.5GB for whatever I see fit.

I used the Gparted live cd (version 0.2.5-1). Version 0.2.5-2 is out but I couldn't get it to boot. It couldn't find the kernel and after I pointed there, I got a kernel panic. The slightly older version also couldn't find the kernel but worked fine once pointed there.

For anyone in the same boat I just typed: 

```
linux initrd=/isolinux/initrd.gz
```

Besides that unexpected hassle, it was perfect. It boots up to a desktop environment quite swiftly and the process of resizing and creating partitions couldn't be easier (or faster)! :wink: 

Tony.

---

