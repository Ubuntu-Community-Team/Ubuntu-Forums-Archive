---
title: "Lost many files in /etc after dist-upgrade"
date: 2015-09-03
forum: General Help
---

### Post by sylwester on 2015-09-03
I got a brand new laptop which I dual boot with Win7 and use Win7 boot loader with full disk encryption on both systems. For Ubuntu I followed a how-to since i couldn't use the whole disk. I like a homogenous environment so I currently use 14.4 everywhere. The laptop has been working since July and been updating it regularly and I haven't had problems with it until today.

Today I did a apt-get update and apt-get dist-upgrade since UI had a warning icon and usually using terminal shows whatever the problem would be, but today it upgarded 4-5 packages and indicated that I needed to reboot, which I did. 

When rebooting I have full disk encryption and it seemed it managed to open sda4 ok, but never passed the waiting splash. I then tried to start without the splash and found tere were lots of strange errors. Files were not found so I figured it might be something fishy about the ext4 file system. I tried to boot recovery but that didn't work either so I had to find a bootable live usb and open the disk from there.

Doing a fsck on the device said the disk was ok so I mounted it and chroot in. Inside the prompt indicated that it didn't know uid 0, which is a bad thing, so I went back to the live cd and looked at /mnt/etc and found that neither passwd og group were present. In all I only had 150 filed in /etc. Actually whole directories, like /etc/apt were gone. 

I restored passwd and group from their *- backups, but I wonder if there is a way to install the default /etc/ files for the config files that I miss? I do get something when i do dpkg --get-selections so it knows what packages are installed. 

Thanks!

---

