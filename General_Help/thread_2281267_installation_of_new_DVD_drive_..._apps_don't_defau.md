---
title: "installation of new DVD drive ... apps don't default to it!"
date: 2015-06-05
forum: General Help
---

### Post by Old Jimma on 2015-06-05
Hi Community:

My DVD drive died. It is definitely dead. :|

I bought a new DVD, and new SATA cable, and a new power cable, and now the DVD opens and closes. I can find the drive on Nautilus, it seems to be **[COLOR="#FF0000"]cdda://sr0/[/COLOR]** :p

I can open the drive from Nautilus, and when the DVD drive has an audio CD, I can click on a wav file... and Videos plays it nicely. :)

However, programs like VLC and K3B can't find the drive. :confused:

How do I tell my computer where the device is so the VLC, K3b, Rhythmbox, etc can find it automatically?? ](*,)

Thanks!
Old Jimma
(Should have Retired by now to the Old Country)

---

### Post by mc4man on 2015-06-05
If still with issue in some players - run this, look for the 2 logical name: entries under -*cdrom section
```
sudo lshw -c disk
```

Make sure your players use one or the other.
Ex vlc in screen (Tools > Preferences > Input/Codecs > Optical drive, don't forget to click 'Save' if changing..

---

