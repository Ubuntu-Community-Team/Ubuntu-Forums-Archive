---
title: "Sound trouble with sony VGN-T240P"
date: 2008-03-31
forum: General Help
---

### Post by Smith101 on 2008-03-31
Hi guys I've search the forums and I've become aware that some people are having the same trouble I am with the Sony VGN-T240P when it comes to sound the I've fiddled around with the basics but nothing seems to work.

The thing I'm looking at is updating the Alsa, Synaptic only has up until 1.0.14 I want to update it to 1.0.16 to see if that will fix the problem. 

So how to I tell synaptic to update it from there or do I need to execute from the terminal if so how would I go about that.

Thanks

---

### Post by superprash2003 on 2008-04-01
hope this works for you [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by Tews on 2008-04-01
I also had problems with sound in my Sony Vaio.. I solved it with this mod ... Hope it helps


Code:

gksudo gedit /etc/modprobe.d/alsa-base

And in the last line of the file, add this line:
Code:

options snd-hda-intel model=vaio position_fix=0

---

### Post by dishguy123 on 2008-06-08
I tried adding that line in my vaio vgn-t370p, but it didn't solve the problem.  there's still no sound.  please help!

---

