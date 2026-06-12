---
title: "so would this work for a dualboot scenario?"
date: 2007-03-05
forum: General Help
---

### Post by pixeldotz on 2007-03-05
so i totally formatted my new laptops hdd essentially destroying windows vista :) just like i wanted.

i put on ubuntu and have been absolutely satisfied with it, even put on ndiswrapper and 915 res for the video.

now for the sad part. i need winxp on here to be able to record with my onboard soundcard (hda-intel) which alsa does not fully support yet. audio and headphones work but the mic does not.

now for the good part. i know if i start fresh and install xp first, then partition and install ubuntu that i will have no problems; BUT i do not want to setup all the ndiswrapper stuff up again. i was thinking of partitioning the drive then doing this code to to backup my mbr with the new partition scheme.

```
sudo dd if=/dev/sda of=/home/ubuntu/OLDMBR.img bs=446 count=1
```

once that is done i could install winxp on the new partition, but xp will destroy the grub loader (from all accounts i've read on this forum). if that happens i could boot back into ubuntu using the livecd and restore the mbr (with the new partition info) with

```
sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/sda bs=446 count=1
```

but from a usb stick of course.

and grub would detect all the file systems right? or at the worst i could edit the menu.lst to recognize winxp.

would this work?

---

### Post by bernied on 2007-03-05
This is all good - it's good to be prepared, but...
When you partition the drive, how are you going to do this?
What is your current partitioning scheme and what will be the future? 
Are you intending to move the ubuntu install to a different partition (like from the first to the second), keeping in mind that windows likes to be installed on the first partition?

---

### Post by pixeldotz on 2007-03-05
i was planning on this.

run ubuntu live cd
partition using gparted or gtparted i think to keep the ubuntu side all the the same and the new ntfs part at the end of the disk.

reboot, and run the mbr backup code and store the image on my usb stick.

install xp. at this point xp would be the only recognizable os on my laptop.

boot using thel livecd again.

using the restore code to restore the mbr, since this mbr would have the partition info saved from AFTER i created the ntfs partition.

reboot  and grub should see all my os', from my understanding grub autodetects and rewrites the menu.lst as needed. if not i could just boot back into ubuntu and add winxp to the list.

all this might be in vain if i can get my mixer to work in ubuntu through the usb (alesis usb) until alsa adds more support for my soundcard.

thanks for the heads up and being prepared though.

---

### Post by bernied on 2007-03-05
The only difficult bit I see is windows - will it let you install into a later partition? One thing that might help is to mark it (the ntfs partition) bootable before you let the windows install cd see it. That should be an option in gparted. You will need to use a primary partition for windows - I'm pretty sure it will not install on a logical partition (inside an extended partition) at all.

Grub won't autodetect and rewrite your menu.lst file unless you tell it to, or you install a new kernel. You can tell it to like this:
```
sudo update-grub
```

If it doesn't give you a windows entry you'll need to manually edit the /boot/grub/menu.lst file. But you can come back here if you get to that point.

You might want to take a look at your /etc/fstab file while you're in that live-cd (or even before you start). Make sure it makes sense with the new partition scheme.

And make sure you've got a way to access the internet in case things go tits-up. If the live-cd gives you internet, then you're set.

You'll have read somewhere that you should back up everything before you start a venture like this. Personally I never bother, but then I suffer and moan when I lose stuff.

---

