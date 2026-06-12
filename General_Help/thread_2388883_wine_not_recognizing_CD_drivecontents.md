---
title: "wine not recognizing CD drive/contents"
date: 2018-04-08
forum: General Help
---

### Post by jamesisin on 2018-04-08
I use EAC to extract audio from my CD's.  Lately wine has stopped associating with my CD drive.  I have tried manually setting the drive in wine config and I've tried all the same using a USB CD drive.  I can open the CD in Nautilus and play the music with VLC without issue.  Just wine and thus EAC are not able to see it.  (EAC reports there is no audio CD in the drive, but it reports that even when wine has no CD drive entry.)

Ubuntu 16.04 fully up to date.

---

### Post by shantiq on 2018-04-09
Hi James [responding to message here as might be of use to others too]

I suggest you go through every step of the stages [here]("https://ubuntuforums.org/showthread.php?t=2092214&p=12392385#post12392385") one more time maybe

all the [B]regsvr32 sql*
[/B]and all sudo mkdir /media/cdrom0 routine   maybe do 2 different ones

does not take long

this is what my current audio Wine config shows as here if it helps:   cdrom01 the one here

[ATTACH=CONFIG]279223[/ATTACH]

Tell us how you fare. Best of Luck.

HA   also do not forget the [ASPI]("https://ubuntuforums.org/showthread.php?t=2092214&p=12982459#post12982459") thing if you want to use a drive that is not the default one on your puter

---

