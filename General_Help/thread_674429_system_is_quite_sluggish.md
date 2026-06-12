---
title: "system is quite sluggish"
date: 2008-01-21
forum: General Help
---

### Post by brook adams on 2008-01-21
Hi There,

I have a 7.10 install that is slow as molasses and I'm trying to figure out why.

Here's the story so far...

The hardware is not too great but a previous install of 7.4 was much more lively.

This computer is assembled out of junk basically. There is a Celeron processor running at 1+Gig, only 256 MB of Ram, a used 30G hard drive and a Toshiba combo drive that came out of a laptop. It's a SCSI drive but it's hooked up to the IDE ribbon with a little 50 pin adaptor. All this on a tiny little motherboard in a little black box. I think it was a cash register or some kinda workstation in it's last life.

I got the machine so I could learn Linux and I don't really know much yet but I have done these things...

I checked to see if I had any extra processes running but that seemed to be ok. I shut down all but the essential services. I looked at the system log which I don't really understand but I do find many entries which look like this...
Jan 21 15:04:14 ComputerName NetworkManager: <debug> [1200956654.784028] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_CDRW/DVD_TSL462D'). 

So my two questions are 1) what does the <debug> entry mean ?and 2) could the SCSI drive be causing trouble?

Thanks to whoever may have some ideas about this.

Brook Adams

---

### Post by ramjet_1953 on 2008-01-21
Hi, Brooke!

The reason that you are having problems is that you are really pushing the envelope with such a small amount of RAM.

Check out this link for system requirements:

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

What I suggest that you do is to install a lighter desktop, such as xfce.

Regards,
Roger :cool:

---

