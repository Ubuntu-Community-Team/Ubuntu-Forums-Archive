---
title: "Terrible sound quality"
date: 2005-07-05
forum: General Help
---

### Post by Jela on 2005-07-05
Hallo!

To put it short: My sound "works", but is terrible.

I am a person tha can not tell the difference of a 32 kbs to a 320 kbs mp3, or a pocket radio to a hifi studio, but THIS is unstandable: Somehow the low frequencies tremble and vibrate STRONGLY, making songs hardly recognizable.

No matter if XMMS, vlc or even Winamp under Wine, no matter if ALSA or ESD or whatever Output I can choose from the menu. I made for lack of knowledge no special audio configurations until now.

Important Data:
Soundcard: Creative SB Life! Value, works perfectly under Win98 and XP,
OS: Ubuntu 5.04
User: Linux Newbie that has no plan of sound at all.

I gladly post more tech specs of hard/software, if somebaody tells my where to find them (this kind of "post the content of your xyz.conf"...)

I would be grateful for some hints about things I could try...
Thanks in advance,
Jela

---

### Post by Karlos on 2005-07-05
Sound in ubuntu requires software mixing and a bit of tweaking

fortunately it isn't that hard

check out the following threads

[http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=26567&highlight=sound)

[http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound](http://www.ubuntuforums.org/showthread.php?t=32063&highlight=sound)

if you wanna use midi

[http://www.ubuntuforums.org/showthread.php?t=30963&highlight=midi](http://www.ubuntuforums.org/showthread.php?t=30963&highlight=midi)

I found all the above very helpful

regards

Karlos

---

### Post by DancingSun on 2005-07-05
I think you just need to turn down the PCM volumn.  For me, if it goes beyond 75-80%, the sound will start to distort.

---

### Post by Jela on 2005-07-05
Wow, thank you, DancingSun, this indeed solved the problem.
(even if it took me some time to find out, what and where is "PCM volume"...

 If somebody reads this that had the same Problem: You reach it by typing "alsamixer" in a terminal, and then moving with the right curser until you reach PCM. It seems also to be accessed by the volume-thing of xmms, while the volume-thing of gnome accesses the "Master" volume, what is indeed somehow coherent...)

I feel a bit silly, but it was really SO distorted, that I never thought it could be just a matter of the volume.
Thanks nevertheless!!

Jela

---

### Post by DancingSun on 2005-07-05
[QUOTE=Jela]even if it took me some time to find out, what and where is "PCM volume"...[/QUOTE]

Oops! In my haste I forgot to give you directions to how to get to the volumn panel!  Sorry about that!

But you can reach the volumn control panel simply by double-clicking on the volumn icon in the top gnome panel.   Or by right-clicking and selecting the appopriate option (I forgot the name/wording  ](*,) ).  You should see PCM as one of the volumn adjusting options (well, at least it's an option for my RealTek OSS and nVidia ALSA drivers).

Edit:
It is possible that this has to do with the inadequate open source sound drivers, as this never happens with my Windows2K and now XP.  So be sure to nag your soundcard/chip manufacturer to release quality Linux drivers!  Preferably ALSA ones.

---

