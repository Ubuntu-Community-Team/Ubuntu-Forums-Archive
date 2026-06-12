---
title: "While Making a Startup Disk-Error"
date: 2013-08-11
forum: General Help
---

### Post by nachinew on 2013-08-11
Hi,


I plan to Make a USB start up disk, So I plan to Select a ISO and then choose Erase disk, while erase I got a Error (Figure 1) which is shown below, after getting this error i skipped the erasing disk part, so i jumped to Start up disk now, while clicking start up disk i got another error (Figure 2), Please share your suggestion.

---

### Post by sanderj on 2013-08-11
I see no figures.

Which program do you use to create the USB disk?

---

### Post by nachinew on 2013-08-11
> **sanderj said:**
> I see no figures.

Which program do you use to create the USB disk?

sorry forget 2 insert.
I am using Startup Disk Creator.

here is the shot the figure

[IMG]http://s13.postimg.org/wiz7maj2f/What_is_this_error.png[/IMG]

[IMG]http://s22.postimg.org/bxguil5sx/What_is_this_error1.png[/IMG]

---

### Post by sanderj on 2013-08-11
Forget usb-creator-gtk / Startup Disk Creator: it has grown into a horribly buggy program.

Use 'unetbootin' instead. Less beautiful program, less beautiful result, but it Just Works.

HTH

---

### Post by The Cog on 2013-08-11
For a year or more, I have just been using dd to copy the ISO image to the stick. Like this:
```
sudo dd if=ubuntu-whatever.iso of=/dev/sdb bs=1M
```
Just **be very sure** that you write to the correct drive letter. This command will show what's there:
```
sudo parted -l
```

---

### Post by nachinew on 2013-08-12
> **The Cog said:**
> For a year or more, I have just been using dd to copy the ISO image to the stick. Like this:
```
sudo dd if=ubuntu-whatever.iso of=/dev/sdb bs=1M
```
Just **be very sure** that you write to the correct drive letter. This command will show what's there:
```
sudo parted -l
```

I tried both things could not work for me.

---

### Post by VMC on 2013-08-12
> **The Cog said:**
> For a year or more, I have just been using dd to copy the ISO image to the stick. Like this:
```
sudo dd if=ubuntu-whatever.iso of=/dev/sdb bs=1M
```
Just **be very sure** that you write to the correct drive letter. This command will show what's there:
```
sudo parted -l
```
I do the same whenever I use usb flash disks. Now I normally just use loopback from grub2.

---

### Post by nachinew on 2013-08-12
> **VMC said:**
> I do the same whenever I use usb flash disks. Now I normally just use loopback from grub2.

But after restart USB option is not enabled in BIOS what should I do

---

### Post by sanderj on 2013-08-12
I see this thread is not going the unetbootin path (the thing I advices), so I'll unsubscribe now.

---

### Post by VMC on 2013-08-12
> **nachinew said:**
> But after restart USB option is not enabled in BIOS what should I do
I'm not quite sure what your asking. If USB is not enabled in BIOS, then enable it.

Are your trying to make a startup disk from an already installed Ubuntu?

---

