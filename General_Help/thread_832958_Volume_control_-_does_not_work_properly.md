---
title: "Volume control - does not work properly"
date: 2008-06-18
forum: General Help
---

### Post by jakupl on 2008-06-18
I cannot use the volume control applet.
I have posted a short video describing it [here]("http://www.youtube.com/watch?v=lYRLYI0tbLI"). 

thanks in advance.

---

### Post by Pjotr123 on 2008-06-18
Weird problem. Try alsamixergui, maybe that'll work:
[http://ubuntutip.googlepages.com/sound](http://ubuntutip.googlepages.com/sound)

---

### Post by danwood76 on 2008-06-18
It could be that its selected a volume control that it cant actually change.

If you open up the volume control do any of the sliders change your volume?
If they do, right click the volume control applet and click prefrences and select that as your volume control, the slider will then work.

---

### Post by jakupl on 2008-06-20
I can right click the volume control and change it from realtech alc600 to alsa pcm.


At first I thought it worked. The slider thingy works perfectly, the volume changes, when the sound is coming from totem, but not with sound coming from any browser... ?

---

### Post by danwood76 on 2008-06-21
This might be a pulse audio issue, pulse audio is like a layer between your applications and you sound card. You can use it to individually set volumes of each app and route audio round your house.

Check this guide for setting up pulse audio properly:
[http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by waggish on 2008-06-22
I've the same problem :(

---

