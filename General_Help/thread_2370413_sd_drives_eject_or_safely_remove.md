---
title: "sd drives: eject or safely remove?"
date: 2017-09-03
forum: General Help
---

### Post by seekertom on 2017-09-03
After viewing my various usb sd drives, I rt clk to begin process of removing them. Sometimes the rt clk menu shows eject, sometimes safely remove, and sometimes both options.

1st, why the differences in options?

2nd, obviously, if only one option, then that's what I need to do, but

3rd, if I have both options listed, which one is correct or more-correct than the other, or doesn't it matter?

hope you can help.
st):P

This helpful info will get me thru the day.
Thanks, folks! I might just find a candle in all this darkness.
st
st

---

### Post by deadflowr on 2017-09-03
usb/flash drives should use safely remove.
dvd/cd should use eject.

More here: [https://askubuntu.com/questions/86019/what-is-the-difference-between-eject-and-safely-remove-device]("https://askubuntu.com/questions/86019/what-is-the-difference-between-eject-and-safely-remove-device")

---

### Post by seekertom on 2017-09-04
I understand that. However, the question is, in part, why are the menu choices different from time to time? My lt has no cd/dvd drive, so actually, eject isn't appropriate for my machine. I agree, sd drives need to be "safely removed", and my question is, why does my ubie sometimes offer me only "Eject"?
thanks, st

---

### Post by vasa1 on 2017-09-04
What is "ubie"?

---

### Post by mc4man on 2017-09-04
This has been going on for years, really no great difference between the 2. When getting both I usually pick safely.

Why the diff options?
Well in the case of getting either eject or safely remove that's easy - 
eject only - drive reports as a SCSI removable disk
safely remove only - drive reports as a SCSI disk

As far as both, no real clue. The drive will report "SCSI removable disk" so it gets eject. It also must present something else so also seen as a SCSI disk", ala  it also gets the safely remove option

There are very old bugs concerning this in LP & Bugzilla, pretty much like a dog chasing it's tail, waste of time to pursue..

---

### Post by uRock on 2017-09-04
I use both for disconnecting and haven't had any issues. I'd rather have functions that overlap and work without error, than have a device not get any options at all.

---

### Post by mc4man on 2017-09-04
What I do find curious is that all usb drives are reported from kernel as ' Fs was not properly unmounted and some data may be corrupt' (message may vary slightly..
Doesn't matter how removed, either from gui or command line.
Can be seen if one runs an fsck on, though again this is likely of no importance & possibly meaningless..

ex.
sudo fsck /dev/sdc1
fsck from util-linux 2.27.1
fsck.fat 3.0.28 (2015-05-16)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 2
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (offset:original/backup)
  65:01/00
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
/dev/sdc1: 76 files, 93652/249875 clusters

---

### Post by seekertom on 2017-09-04
One might say he's using the operating system windows 7, or, maybe win 7. I kinda like ubie, probably because it's nicer to say when discussing ubuntu version 14.04, or ubuntu 16.02, or ubuntu 17.04, with the bunch of old folks I work for. Hope it's not offensive to anyone here!
st

---

