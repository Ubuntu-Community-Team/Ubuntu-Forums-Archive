---
title: "Is there a way to get an Ubuntu machine to act like a USB Mass storage device?"
date: 2008-03-10
forum: General Help
---

### Post by Rich Stokes on 2008-03-10
Guys,

I have a machine running ubuntu which I want to be able to use as a USB mass storage device.  That is, I want to connect it to another machine via a USB cable and be able to have part of that machines hard drive appear as if it was a USB mass storage device.

Strange request, I know, but is there a way to do this?

Thanks,

Rich

---

### Post by mrsteveman1 on 2008-03-10
Sort of like target disk mode on a mac etc. It should be possible to do something like this with Firewire, but only when the machine is on and only for disks that aren't mounted, IE not the system disk.

USB was never intended to be a point to point sort of thing, there are master and slave devices with USB which is partly why the connectors on each end are different. It would also be technically non standard because the normal USB cables can't be used to connect 2 machines directly to each other. They do make those weird "transfer" cables but thats special and doesn't actually provide access to a machines disks as if it were just another disk.


I do know you can do this sort of thing with [ATA over ethernet]("http://en.wikipedia.org/wiki/ATA_over_Ethernet").

---

### Post by forestpixie on 2008-03-10
Can you not network them?

Nice to see someone who's close to home :)

---

### Post by Rich Stokes on 2008-03-10
> **forestpixie said:**
> Can you not network them?

The requirement is a bit esoteric to be honest.  I'd ideally need to be able to drop things into a network share so that they appear on the "USB device", if that makes sense.  Imagine being able to add stuff to a USB stick stuck in a machine so that that machine can read it.

Not vital, and I assume not possible, but it'd be a neat trick if I could pull it off :)

> **forestpixie said:**
> Nice to see someone who's close to home :)

Yeah, currently happy I live on a hill (after last night's torrential downpour!)

---

### Post by forestpixie on 2008-03-10
> Yeah, currently happy I live on a hill (after last night's torrential downpour!)

yea - little bit damp I'd say - although it doesn't appear to have caused to much trouble locally at least, although I haven't been to see what's happened at Hurst Castle yet - about 90mph at the Needles apparently.

But as far as the USB thing goes I'd be looking at mrstevman's post, sorry can't be of more help - just thought I'd say hello as you're now a neighbour :)

---

### Post by koenn on 2008-03-10
Here are some bits and pieces :
Have a look at this : [http://www.linux-usb.org/usbnet/](http://www.linux-usb.org/usbnet/)  ,  

It talks a lot about those "transfer" cables but it does at the same time explain that the linux kernel supports "usbnet" - allowing you to run IP over an USB bus, so theoretically you could do NFS or samba over IP over USB to implement your mass storage USB device.
see maybe also this : [http://www.qbik.ch/usb/devices/showdr.php?id=62](http://www.qbik.ch/usb/devices/showdr.php?id=62)


A lot of USB devices also run Linux, and this should be open source and maybe even documented so, to the extend that these devices present themselves as storage,  you might be able to apply something similar  to a PC

---

### Post by Rich Stokes on 2008-03-11
Thanks for the input guys.

---

