---
title: "Using Ipod 5th gen (video) as bootable media."
date: 2015-04-30
forum: General Help
---

### Post by CaptainMark on 2015-04-30
At work I have a pc that boots to a live USB instead of the onboard hdd. The live usb works but is a less than desirable option, it can't be updated and is prone to freezing after a few hours. I have an old ipod lying around at home and was hoping to use this as an external hdd and do a full install onto it. I proceeded to plug the ipod into the pc, on the live session, it appears as an external drive easily enough, I was able to use fdisk easily enough to wipe the drive create a partition, make it bootable and use the live session installer to install ubuntu onto the ipod, all seemed to go well until I rebooted and found that it doesn't show as a bootable media, it appears normally when running ubuntu I can mount it but I simply cannot boot from it.

Does anyone have any experience and/or any advice on what to try, I've tried a few things so I'll list them below.

Tried:
MBR and GPT partitioning
Having a boot partition
Using Vfat and Ext partitions
Using the ipods "disk mode" (doesn't behave any differently)
Powering usb ports when computer is off

I'm thinking perhaps that the ipod has some kind of lower level hidden partition that I'm not seeing, the ipod still functions as an ipod when I unplug it which i wasn't expecting

Any help?
Regards
Mark

---

