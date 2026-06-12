---
title: "Replacing Windows 8 With Ubuntu On Acer PC"
date: 2013-12-09
forum: General Help
---

### Post by Vannyi on 2013-12-09
I'm looking to buy this Acer PC ([http://www.futureshop.ca/en-CA/product/acer-acer-axc-605-desktop-pc-intel-core-i3-4130-1tb-hdd-4gb-ram-windows-8-axc-605-er30/10268447.aspx?path=6f31c0e75bb37d44043d3ba3f17705a3en02](http://www.futureshop.ca/en-CA/product/acer-acer-axc-605-desktop-pc-intel-core-i3-4130-1tb-hdd-4gb-ram-windows-8-axc-605-er30/10268447.aspx?path=6f31c0e75bb37d44043d3ba3f17705a3en02))

I really don't want Windows 8 and was looking to replace it with Ubuntu.  I'm just wondering how successful this might be if I format the drive and install Ubuntu?  Is there any kind of compatibility test that would verify if Ubuntu would work and is there anything I need to be aware of?

Thank you

---

### Post by PaulBx on 2013-12-10
Boot off the CD (I use puppy linux but there must be an ubuntu equivalent), then plug in a USB backup drive and use "dd" command to generate an image file of your hard drive on the USB backup drive. Then remove the USB backup drive and install ubuntu on the hard drive and play with it. If you can't get it working you can always boot with puppy again and roll the backup image back on to the hard drive so it will be a Windows machine again.

I always do an image backup before doing anything risky. You could try a dual-boot setup instead of wiping Windows completely.

Alternately, just remove the standard hard drive and get a new one and install it and put Ubuntu on it. Hardware is getting pretty cheap these days.

Usually these desktop systems are the easiest for getting Linux running.

---

### Post by electrohandyman501 on 2013-12-10
As far as compatability, if/when you actually get the machine TRY a LiveCD/USB before you do anything with the original win8 system. Then, and I'm pretty sure it should, if the live boot works with all of the included hardware, you can consider your options for dual boot, wipe and format, or as was suggested above, a clone copy to an external disk, or a completely new hard drive for the new OS.

---

