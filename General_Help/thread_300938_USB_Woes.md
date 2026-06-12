---
title: "USB Woes"
date: 2006-11-16
forum: General Help
---

### Post by timhaughton on 2006-11-16
Here's the thing:

I have a server at home. It's not a fancy thing, just a little x64 box that sits in a cupboard. It has no keyboard or monitor attached.

The server has two external hard drives attached via USB. They dont hot swap, they just sit there.

The first thing I noticed was that the USB drives did not get automagically mounted when I connected them. No biggy, could mount them just fine myself.

When I was converting the drives from NTFS to Ext3, I was accidentally caught out by a change in the probe order and formatted the wrong one, losing a lot of data - not mission critical stuff, but you know.

To pin the drives down a little more, I added some entries into fstab identifying the drives by UUID so I'd always know where I stood.

The problem is only one of the drives is detected at boot. The other one I have to power down the power up in order for it to be recognised. Because of this, the system is failing at boot whilst going through fstab. This means that in order to reboot my machine, I have to comment out the lines in fstab, then reboot, power cylcle one of the drives, uncomment the lines in fstab then do a sudo mount -all.

This is obviously a pain in the neck. Added to this is the fact I can't reboot the server remotely (not that I would really need to).

So to clarify, I think the main problem is that after booting, lsusb shows only one of the drives.

Is there a way to force it to find the drives at boot? And is there a more suitable way to pin permenantly attached USB drives to a mount point?

Cheers,

Tim

---

