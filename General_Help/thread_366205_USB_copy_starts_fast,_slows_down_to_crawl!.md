---
title: "USB copy starts fast, slows down to crawl!"
date: 2007-02-20
forum: General Help
---

### Post by capdog on 2007-02-20
Hey everyone...

Strange one today. I've got a flash drive and I wanna copy a 800 meg file onto it. It's 2 gigs, and is mounted as follows:

```
/dev/sdb1 on /media/2GIGFLASH type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
```

I start copying the file using the cp command, and in another terminal I run ```
watch -n 0.5 ls -hl
``` which basically just shows me a directory listing every .5 seconds, so I can see how the file is growing on the flash drive.

The thing is, the first 300 - 400 megs is copied so quickly, but then the process gets slower and slower until it's absolutely crawling! It ends up taking about 5 minutes, whereas it should take all of 1 minute to copy.

Anyone got any ideas? Is this a bug?

Cheers
capdog

---

### Post by dcstar on 2007-02-20
> **capdog said:**
> Hey everyone...

Strange one today. I've got a flash drive and I wanna copy a 800 meg file onto it. It's 2 gigs, and is mounted as follows:

```
/dev/sdb1 on /media/2GIGFLASH type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
```

I start copying the file using the cp command, and in another terminal I run ```
watch -n 0.5 ls -hl
``` which basically just shows me a directory listing every .5 seconds, so I can see how the file is growing on the flash drive.

The thing is, the first 300 - 400 megs is copied so quickly, but then the process gets slower and slower until it's absolutely crawling! It ends up taking about 5 minutes, whereas it should take all of 1 minute to copy.

Anyone got any ideas? Is this a bug?

Cheers
capdog

When you copy the data is actually written to a cache, and then Linux pushes it out to the USB device (as fast as the USB device can absorb it!).

What you are seeing is the cache filling up extremely quickly, and then when there is no more space you have to wait for actual data in the cache to be written to the USB device before more space is available - when this occurs you experience the actual write speed of your USB device.     :( 

Even when the write seems complete, if you try and unmount the USB device it will take many minutes to do because unwritten data in the cache is now being flushed to the device - usually this occurs in the background so you don't notice the delay.

---

### Post by capdog on 2007-02-21
Interesting, thanks for the response.

Without doing any controlled experiments, I would say there is something wrong with my system. The USB is not performing as well as it does in Windows. I will investigate further and report back!

---

### Post by martinquested on 2007-03-05
Hi,

had any luck with this yet?  I have a device which is very slow copying [B]from[B] the device to my linux box.  I initially thought it was because the device is USB 1.1, but then I realised that doesn't explain why the transfer is super-quick if I use Windows XP.

Would dearly love to get this sorted; if you have any pointers, let me know!

Cheers.

mQ

---

