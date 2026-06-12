---
title: "Custom LiveCD"
date: 2006-11-06
forum: General Help
---

### Post by nuthinking on 2006-11-06
Hi Guys, I'm new to Ubuntu, and Linux in general. Sometimes I develop Java applets that use OpenGL. With Ubuntu 6.10 the installation of Java was very smooth comparing to 6.06 and thus the applets ran straight away. Btw, it would be very cool if I could create a LiveCD (on a usb key) with Java installed and maybe also with my applets, so I could make my applets run easily to any computer. Would it be possible or I'm just dreaming? LiveCD really impressed me and it would be cool to understand how it works and its limitation (any link?).

I read that from 6.06, thanks to the "persistence", it is possible to install other softwares on USB drives, for instance, when running the LiveCD, I presume it wouldn't work for low level applications like Java, would it? If it would, it could be enough to create two partitions on the usb key one with the liveCD and the other where I will install later the softwares.

Does it make any sense? Please give me some good news :)

Thanks a lot for the attention, chr

---

### Post by John.Michael.Kane on 2006-11-06
Have a look
[http://reconstructor.aperantis.com/](http://reconstructor.aperantis.com/)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28usb%29](https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28usb%29)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by nuthinking on 2006-11-06
Thanks a lot, I'll check them and then let you know how it goes.

---

### Post by nuthinking on 2006-11-06
I followed the tutorial LiveUsbPendrivePersistent and unfortunately didn't work.

What I get is:

On my old laptop Acer, nothing the usb is totally ignored (of course I changed the boot order)

On my new laptop Dell, after I changed the order (and from the BIOS I was also able to set if bootable) a black screen appeared with only the following text:

;

and if typing i could only add ;'s becoming something like:

;;;;;;;;;;;;;


I'm trying with 6.10 and the difference I did compare the tutorial were:

- file system, because the comment I did w95/FAT 16 (LB) (or something similar)

- I had problem to copy a couple of files from the "dist" folder on linux, but on Windows XP I should have copied them.

- In the syslinux, as suggested, I replaced 'preseed/ltsp.seed' by 'preseed/ubuntu.seed'

- I tried the lilo command suggested at the end but it couldn't find the command.

Is there a way to see if my key can boot? The fact that my new machine tried from there maybe is a good sign, but so what else could be the problem?

---

### Post by nuthinking on 2006-11-08
I tried also to following the Windows instructions from the same tutorial but didn't work. 

Reconstructor is a really cool software but probably I don't need it, since with the persistence I could add my softwares later.

So I presume I have to find a way to make the liveCD in a USB partition first. Any other link maybe with specific instructions for Edgy and understandable for beginners like me?

Thanks, chr

---

### Post by handy on 2006-11-08
Have a search, there is a Looong running thread that made great headway in using usb drives with liveCD's installed on them, these usb drives will boot on many different motherboards too!

---

### Post by handy on 2006-11-08
It took me a while but I found the thread, if you skim it from the start you will get some other good links out of it as well as the thread itself.

[http://ubuntuforums.org/showthread.php?t=71567](http://ubuntuforums.org/showthread.php?t=71567)

---

### Post by nuthinking on 2006-11-08
Thanks a lot Handy for the link, tonight I will have a go and let you know.

chr

---

### Post by nuthinking on 2006-11-08
I had a look and it seems that it is still a very instable solution and what I see seems to be process that got to the [tutorial ]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent?highlight=%28usb%29") I followed and that didn't work.
That could be a very powerful feature and it's a shame to see that it is still far to be standardize.

---

### Post by handy on 2006-11-09
If it doesn't suit you yet? That's ok, the thing that matters is that it is only a matter of time, & without a doubt what you require will become old hat!

Before you know it, our imaginations are seeing something far more useful & stimulating. :KS

---

### Post by nuthinking on 2006-11-12
Actually today we managed to make the usb key boot works. The only thing is that ubuntu doesn't save any settings in the casper-rw partition :(
Any ideas what it could be?

Thanks, chr

---

