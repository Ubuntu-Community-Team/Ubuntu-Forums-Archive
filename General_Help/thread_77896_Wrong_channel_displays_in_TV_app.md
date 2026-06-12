---
title: "Wrong channel displays in TV app"
date: 2005-10-17
forum: General Help
---

### Post by joey7855 on 2005-10-17
Hello! I've been using different flavors of linux for a while now but am still a newbie by all definitions of the word. I installed breezy this morning and everything works but my tv card. I installed tvtime to watch tv and after it scanned for all my channels, the problems started happening. First, the picture is mostly black and white with hints of color sometimes. Then, the channels are all off. For example, channel 39 is supposed to be channel 38 and channel 12 is supposed to be channel 99. I'm using a ATI TV Wonder VE and I need some help getting this working! Thanks!

Specs:
AMD Athlon XP 2500+
512 MB RAM
NVIDIA GeForce 5500 256MB AGP
ATI TV Wonder VE
Seagate Barracuda 160GB
WD 120GB
Sony DVD+RW
Sony DVD-ROM
Ubuntu Breezy
Windows XP

---

### Post by wenzlicker on 2006-06-28
I had the same problem. This is how I fixed it.

[HERE]("http://ubuntuforums.org/showthread.php?t=119680&highlight=tvtime+color")

and

[HERE]("http://www.ubuntuforums.org/showthread.php?t=107932&highlight=bttv")

and

[HERE]("http://xawdecode.sourceforge.net/aideUS/htmlpage/TVCardall.htm")

Remeber, if you live inside the USA, you have NTSC (for my card it was tuner 2). In the above links, there are links to card and tuner lists. find the right tuner/card combination and put it in the bttv file as described. One of the articles says no restart is need ("sudo modprobe -r bttv to unload sudo modprobe bttv to load"). This did NOT work for me. I had to do a restart.

Upon restarting, run tvtime-scanner. It takes a while, but if you have the right options in your bttv file, you should have color and correct channels. I hope this works for you. It took me a while, but i finally got it working for me.

Happy watching.

---

