---
title: "Ubuntu worked at first... now... not so much..."
date: 2013-06-20
forum: General Help
---

### Post by Linux_n00b on 2013-06-20
So I installed Ubuntu 12.04.2 to a USB drive.  Worked great on my Dell E4310 and also on my HP dv6700 that night.  

Today when I got to work, I docked my E4310 to my docking station and booted from my USB drive and I got the black screen boot.  So I rebooted, tried to edit my grub list for the first entry my removing "quiet splash" and adding "nomodeset" then I hit Ctrl + X to reboot, and this time it gets stuck at:

Begin: Running /scripts/init-bottom ... done.
[ 15.251138] Adding 1395708k swap on /dev/sdb5. Priority:-1 extents:1 across:1395708k

...and goes no further.

If I try and boot to my Ubuntu USB drive on my HP laptop, it works great!  Please help! :(

---

### Post by 2F4U on 2013-06-22
What is different when the laptop is connected to the docking station? Is there additional hardware in the dock such as, for example, a graphics card?

---

### Post by Linux_n00b on 2013-06-23
When plugged into the docking station I have a dial monitor setup (I guess your would consider a graphics card?).  I also have a mouse and keyboard hooked up at well...  I think I forgot to mention, now if I try to boot from the USB drive again without being in the docking station on the E4310, it get stuck at:

Begin: Running /scripts/init-bottom ... done.
[ 15.251138] Adding 1395708k swap on /dev/sdb5. Priority:-1 extents:1 across:1395708k

---

### Post by Bucky Ball on 2013-06-23
How does the machine plug into the docking station? I'm not familiar with them. If it is USB, then there's a chance the machine is trying to boot from the docking station rather than the persistent install on the USB dongle (which I'm presuming is what you have).

Could be way off but I don't know how docking stations connect. ;)

---

### Post by Linux_n00b on 2013-06-23
> **Bucky Ball said:**
> How does the machine plug into the docking station? I'm not familiar with them. If it is USB, then there's a chance the machine is trying to boot from the docking station rather than the persistent install on the USB dongle (which I'm presuming is what you have).

Could be way off but I don't know how docking stations connect. ;)

Uh, these are the best way to describe it:

[http://www.atrlaptops.com/ebay/dock/pr03x_1](http://www.atrlaptops.com/ebay/dock/pr03x_1)

[http://www.dhoomshop.com/image/cache/data/Dell%20Adapters/PW380%20Dell%20Latitude%20E6400%20Docking%20Station-600x500.jpg](http://www.dhoomshop.com/image/cache/data/Dell%20Adapters/PW380%20Dell%20Latitude%20E6400%20Docking%20Station-600x500.jpg)

---

