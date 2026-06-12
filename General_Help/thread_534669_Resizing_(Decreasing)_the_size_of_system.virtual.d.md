---
title: "Resizing (Decreasing) the size of system.virtual.disk"
date: 2007-08-25
forum: General Help
---

### Post by raycosm on 2007-08-25
While downloading a file from the internet, I got an error about not having enough space. So I looked into KInfoCenter, and it said that my /home folder (/media/host/wubi/disks/home.virtual.disk) had no free space left (it was around 900mb). KInfoCenter also told me that the total size of /media/host/wubi/disks/system/virtual.disk was 6100 MB and it had about 3100 MB free.

I want to increase the size of home.virtual.disk about one GB, but not having a lot of space left on my small (30GB) hard drive, I also want to decrease the size of system.virtual.disk about one GB. I tried using toporesize, but if I try to change the size (both increase and decrease) of any of those two virtual disks, nothing happens except it tells me that I should get a better version of e2fsck.

Searching for resizing virtual disks gave me about zero results on decreasing the size of a virtual disk and about a million results on increasing the size of a virtual disk.

Thank you in advance for any help, and thanks for the excellent job on Wubi.

---

### Post by tuxcantfly on 2007-08-25
Use LVPM at [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) , it can resize virtual disks

First shrink your system.virtual.disk, reboot into Windows, see if the new disk works, and if you're short on disk space, you can delete the original and use only the new one (LVPM will give you instructions as it exits)

Then repeat the same process on the home.virtual.disk

---

### Post by raycosm on 2007-08-25
Well I just ran it, and I totally $*&@ed my computer and got blue screens whenever I tried to boot Windows, and freezing up when I tried to boot Kubuntu. It froze halfway into the process of resizing, I think I must have ran out of hard drive space or something because I had 2 GB free, and I chose to resize to 4 GB. I let it run for an hour and just gave up, and shut off the power (the hard drive light hadn't blinked a bit since it froze, so I figured it was safe to just hold the power button down).

I loaded up the recovery partition from Dell, wiped and reinstalled Windows. I didn't lose too many highly important things, just a few pictures and program settings.

You know what I learned from this? I need a new laptop. So tomorrow, I'm going to go get a new one with a 160 GB so I can dual boot Kubuntu and Vista (I hope Vista gets along with Kubuntu).

I thank you for giving me an impulse to buy a new laptop, because I'll probably be happier with it (plus I can hibernate/standby). :)

---

### Post by tuxcantfly on 2007-08-26
> Well I just ran it, and I totally $*&@ed my computer and got blue screens whenever I tried to boot Windows, and freezing up when I tried to boot Kubuntu. It froze halfway into the process of resizing, I think I must have ran out of hard drive space or something because I had 2 GB free, and I chose to resize to 4 GB. I let it run for an hour and just gave up, and shut off the power (the hard drive light hadn't blinked a bit since it froze, so I figured it was safe to just hold the power button down).

Oh crap that doesn't sound good, sorry, I think I'll need to add a disk-space checker into the resizing portion.

---

### Post by raycosm on 2007-08-26
Hahah, well I'm not sad or anything. I'm going to buy myself a new and better laptop, and it's thanks to your help.

---

