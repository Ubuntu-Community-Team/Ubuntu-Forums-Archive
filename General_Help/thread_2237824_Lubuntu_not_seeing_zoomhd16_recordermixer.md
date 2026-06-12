---
title: "Lubuntu not seeing zoomhd16 recorder/mixer"
date: 2014-08-04
forum: General Help
---

### Post by jeff82 on 2014-08-04
Hi all,
ive a fresh install of lubuntu on my laptop, usb drives/devices are seen but not the zoom. It is visible via the lsusb command.
i also noticed some of packages; mount manager, flacon dont seem to exist via the software centre or even in the terminal when i try and install.
do i need to just install ubuntu 14.04? and try again

cheers

something has changed as i can now see it under Disks as other devices its /dev/sdb....not sure how to navigate to it (i just need to take the wav files from it onto my laptop)
cheers

is there anyway in terminal to mount it(make it visible) so i can navigate to it?
surely if its seen in Disks it must be available somehow....please help 
many thanks

sudo mkdir /media/external
and 
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
(as it is FAT32) sorted it

---

