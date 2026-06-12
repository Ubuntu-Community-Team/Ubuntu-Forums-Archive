---
title: "Newbie needs help backing up ubuntu"
date: 2007-06-12
forum: General Help
---

### Post by sookoon on 2007-06-12
Hello, all.  Newbie to Ubuntu.  I finally got everything to work perfectly!  (except for VPN and Logitech USB wireless music (Music Anywhere). 

Now that I have everything just-so, I need to back it up.  The posts I've read about backing up are, perhaps, a bit technical for me.  I simply need to create an OS image (with all the personalizations, settings, etc.), to an external HDD or my 8GB USB key, and need to know also how to restore from that image.

I read about udev's, and such, but apparently it is beyond my capabilities.  I have Norton Ghost 10 - would that work?  if so, how?  I've never used Ghost, even though I have had the CD for a few years...

Thanks all!

---

### Post by indytim on 2007-06-12
My recommendaton is to get (it's in the repositories) Partimage.  It runs from a shell (comman line launch).  It will allow you to backup at an entire partition.  I use it weekly to backup my 7 active ops partitions.

IndyTim

---

### Post by rbmorse on 2007-06-12
How do you get Partimage to backup a mounted partition, or do you manually umount before imaging those 7 active ops partitions?

---

### Post by CautionaryX on 2007-06-12
[http://ubuntuforums.org/showthread.php?t=35087&highlight=how-to+backup+your+system](http://ubuntuforums.org/showthread.php?t=35087&highlight=how-to+backup+your+system)

I would try the method outlined in the link, but change the destination path to your USB drive / external HDD. It took me about 15 mins to change the permissions from root to my account so I could burn the archive to a DVD but, I think it was worth it.

---

### Post by terabite on 2007-06-13
As for preferences... Most of ur preferences are saved in ur Home folder... so u can just back that up.
Note: Themes are saved in a .themes folder (hidden).

As for backing up of downloaded packages:

U can backup all ur .deb files from /var/apt/archives
Else u can download APTonCD. Its a gui application that automatically backs up all downloaded archives and creates an ISO file that u can burn to a CD and use as a third party repository later....
Its available on sourceforge as well as Feisty repos:

```
sudo apt-get install aptoncd
```

---

