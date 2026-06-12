---
title: "Speakers not being used by linux"
date: 2008-04-09
forum: General Help
---

### Post by Dthdealer on 2008-04-09
My mother-board has an in-built speaker which linux uses instead of my speakers on the desk. I've tried plugging my speakers in the head-phone jack but that didn't work either.

A related problem is that the main volume control does nothing, I have to adjust the PCM volume control for the volume to change, and sound does not cease when I set the PCM volume to its lowest, but does stop when I mute the PCM volume.

As far as I know I'm running an HP compaq desktop computer.

---

### Post by Tews on 2008-04-09
I also had problems with sound in my Sony Vaio.. I solved it with this mod ... Hope it helps


> Code:

gksudo gedit /etc/modprobe.d/alsa-base

And in the last line of the file, add this line:
> Code:

options snd-hda-intel model=vaio position_fix=0

You will need to replace "vaio" with the model of your computer...

---

### Post by Dthdealer on 2008-04-19
The only information on my case is [COLOR="Red"]HP Compaq[/COLOR]. Should I enter [COLOR="Red"]compaq,hpcompaq,hp[/COLOR] or something else? I received this computer as second-hand from a stock-market company so I haven't got a clue what model it is as it is not labeled.

---

