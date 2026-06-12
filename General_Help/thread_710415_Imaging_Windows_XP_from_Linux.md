---
title: "Imaging Windows XP from Linux"
date: 2008-02-28
forum: General Help
---

### Post by TorchlightJay on 2008-02-28
Hello, 

I have a dual booted hard drive with XP and Ubuntu. I want to image the installed version of XP onto other machines but don't even know where to start. Any advice? I'd also like to do the same with Ubuntu. Thanks.

---

### Post by CadetD on 2008-02-28
Are you looking to dump the image onto another Virtual machine, physical machine across LAN or physical drive in same machine?

The easiest way would be to use Symantec Ghost or G4l (Ghost4Linux). 
Both can take an image of a hard drive or partition and burn onto another. 
 
If you have both HDDs in the same machine, then you can use the Linux *dd* command to dump the data from one partition to another. This is a very powerful command and if you put the wrong partition, you could overwrite your precious data. 
```

sudo umount *YourPartion* #e.g. /dev/sda1
dd of=/dev/sdb1 if=/dev/sda1 #dump from first of drive b  to first partition of drive a

```

You may want to lookup the dd command before starting:
man dd

To find out what drives and partitions you have, use 
fdisk -l

*** If you are at all uncomfortable, I would stongly suggest that you look at using one of the Ghost products mentioned above. ***

See:
[http://sourceforge.net/projects/g4l]("http://sourceforge.net/projects/g4l")

Hope this helps.

---

### Post by TorchlightJay on 2008-03-03
Not a bad idea. I was wondering, can this work for any operating system or file system, that command you showed me? What if I want to do a net install or put it on a CD/DVD, somehow get the image to another computer. How would I do that? Thanks for your time and help.

---

