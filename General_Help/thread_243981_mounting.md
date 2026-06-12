---
title: "mounting"
date: 2006-08-25
forum: General Help
---

### Post by xander848 on 2006-08-25
I have an external hard drive that gets automatically mounted to "WD Passport" I would like to change where its get automounted because there is a space in there and it gets ridiculosuly annoying using quotes from the terminal.

How would I go about this? Maybe create an fstab entry for it? It's usually not plugged in at startup however so would ubuntu complain that it couldnt mount that harddrive?

---

### Post by goatflyer on 2006-08-25
It will 'complain' only as much as it complains when cd drives are empty.  It won't stop you booting, and when you do show up with the automountable drive, it should mount where your fstab entry says it should.

What I don't get is, where the "WD Passport" name comes from.  Do you already have a directory by that name?  If so - what happens if you rename it?

---

### Post by xander848 on 2006-08-25
Thats the name of the harddrive that the manufacturer put on it. That name shows up in windows as the name of the drive too.

 Sweet I'll try making an fstab entry for it though.

---

### Post by xander848 on 2006-08-25
Ok ran into a problem. The partitions no longer mount automatically.
I can mount them maunally. I checked in Disks and the partition is sda2. I have also creaded the diectory /media/sda2.

Here's my fstab entry:

/dev/sda2	/media/sda2	ext3	defaults	0	0

Any idea whats wrong?

EDIT: I guess I had to maunally mount first using the terminal because it now automounts even after unplugging it and replugging it. Ok thanks for the help!

---

### Post by peabody on 2006-08-25
> **xander848 said:**
> Ok ran into a problem. The partitions no longer mount automatically.
I can mount them maunally. I checked in Disks and the partition is sda2. I have also creaded the diectory /media/sda2.

Here's my fstab entry:

/dev/sda2	/media/sda2	ext3	defaults	0	0

Any idea whats wrong?

EDIT: I guess I had to maunally mount first using the terminal because it now automounts even after unplugging it and replugging it. Ok thanks for the help!

I think you better put it under /mnt not /media.  /media is automagically handled by the hotplug.  Maybe it's smart about it, but I could see there being problems if you ever plug in a drive with the name sd2 (probably not likely I know, but ya never know).

---

