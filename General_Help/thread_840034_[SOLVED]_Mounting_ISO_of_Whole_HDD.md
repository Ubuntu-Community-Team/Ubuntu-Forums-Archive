---
title: "[SOLVED] Mounting ISO of Whole HDD?"
date: 2008-06-25
forum: General Help
---

### Post by hydroxic on 2008-06-25
So a couple months ago, I decided to back up my desktop's entire hard drive. I dd'd it into a raw image (iso file) 
dd if=/dev/sda of=desktop-image.iso
(or something of the sort)

It had multiple partitions: Windows, Data, Ubuntu, etc.. 

I know there's a way to mount a single-partition iso, but does anyone know if there is any way to mount a partition on this disk image?

Ideas?
Or do I have to restore it to a disk to get the data...

---

### Post by attari on 2008-06-25
> **hydroxic said:**
> So a couple months ago, I decided to back up my desktop's entire hard drive. I dd'd it into a raw image (iso file) 
dd if=/dev/sda of=desktop-image.iso
(or something of the sort)

It had multiple partitions: Windows, Data, Ubuntu, etc.. 

I know there's a way to mount a single-partition iso, but does anyone know if there is any way to mount a partition on this disk image?

Ideas?
Or do I have to restore it to a disk to get the data...


AcetoneISO

Get that and more cools apps from here:
[http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications]("http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications")

---

### Post by cariboo on 2008-06-25
No you have to mount the whole image. In a terminal:

```
sudo mount -o loop desktop-image.iso /mnt
```

Jim

---

### Post by p_quarles on 2008-06-25
You should be able to mount a disk image as a loopback device. E.g.:
```
losetup /dev/loop0 /path/to/image/file
```
And then mount /dev/loop0 as you would any other disk. That's how I think it would work, but I've only done this along with crytpsetup -- you may need any an equivalent device manager to make the loopback into a mountable volume.

Also, is this really an ISO 9660 image? I wasn't aware that dd was capable of creating these.

---

### Post by hydroxic on 2008-06-25
Thanks for the input. I'll have to try these when I get back to my other computer. 

@p_quarles: No, it's not an ISO 9660. I just named it as an .iso file - so I guess, ignore the iso part. I just used dd to create an image of my entire drive, not just one partition. 

Sorry for not being totally clear, but the problem is that the flat image that I created has multiple partitions ON it--using several different file systems, etc.. 

Not sure if that makes sense. 

Nevertheless, I will try the solutions you all suggested in a little bit.

---

### Post by hydroxic on 2008-06-25
Well, the losetup loopback device solution worked!

I must have been wrong. I guess I only backed up my Windows (NTFS) partition! The error that showed up told me I had shutdown Windows incorrectly or something, so I forced the mount and it works fine!

Thanks everyone!

---

