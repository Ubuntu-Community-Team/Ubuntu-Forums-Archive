---
title: "How do I format an SD card in 7.10 after Vista had its way with it?"
date: 2008-01-30
forum: General Help
---

### Post by tromik on 2008-01-30
There is an SD card bug in Vista atm. When you use a USB card reader and a 2GB (or over?) SD card, Vista cannot find the card and suggests that you format it. It states the device size at 969mb as opposed to the 1.89gb it actually is.

I formatted the drive in Vista trying to find out why this was - the card is usable in every device I've tried it in so far (mp3 player, DS card reader, 360), but I've basically lost a gig of space.

I put the card in my sister's laptop (running Vista, too) as it has a built-in card reader. I was able to format the card to 1.89gb, but an error occurred as it finished. I tried this three times. A quick format would work, but if I tried to fit more than 969mb on the device, I get a n error.

I'd like to try and fix it in Ubuntu. The card is automatically detected, and other threads here suggest formatting it in GParted. I have GParted, but the SD card is not listed as a device there.

Any suggestions?

---

### Post by MoLE on 2008-02-07
Have you tried other SD cards in the same reader under Ubuntu?
Assuming the reader works and the SD card gets detected it should be recognised as /dev/sdx where x= alphabetical letter.

Gparted should then be able to partition and format the device.

If it can't, then what I would do is go to the commandline (terminal) and type ```
dmesg
``` to work out which device it had been recognised as, say /dev/sdg

then use fdisk thus:
```

fdisk /dev/sdg

```

which should then allow you to view the partition table, change and format as necessary.

If you want to play around with fdisk, you can always make changes, but they are not committed until you specifically say so.  So you can always escape by quitting but without saving changes.

---

