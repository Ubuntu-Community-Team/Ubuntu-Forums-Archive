---
title: "aMSN sound problems on Hardy"
date: 2008-05-09
forum: General Help
---

### Post by fantan on 2008-05-09
Hello Everybody!

I have a problem with the sound of aMSN on my Hardy Heron system.
I configured my sound with help of a HowTo from this forum using pulseaudio. Now everything is works fine apart of aMSN signals. To play signals from aMSN I vhave choosed the snack library. When I try to play the test signal, I've got the following error message:
"Error during playing sound. Could not gain access to /dev/dsp (/dev/dsp1, /dev/audio, /dev/audio1) for writing."
These devices in the /dev directory belong to group audio but till now there wasn't group audio at all. I created group audio but if several applications (audacious, amarok, rhythmbox, etc.) work, I can't play sound in aMSN at all. But the aforementioned applications can play sound alltogether with help of pulseaudio fine.

Can anybody help me please with aMSN sound?

Best regards,
fantan

---

### Post by lesergi on 2008-05-09
Hi!

Do you assign audio group to your user?

---

### Post by fantan on 2008-05-09
Of course I did!:)))) That is I've created the audio group and assigned myself as standalone user to it.

---

### Post by fantan on 2008-05-09
Nobody can help?

What a pity!:(

---

### Post by lesergi on 2008-05-09
Pfff... I'm sorry, but I don't know...

I use "aplay" command in aMSN and it works very fine.

Bye!

---

### Post by macabro22 on 2008-05-31
Lesergy,

I am using aplay as well, but I can't get aMSN message sound notifications when other software such as rhythmbox is accessing the sound card.

Can you post how exactly you use the aplay synthax?

---

### Post by nebulous2008 on 2008-06-02
Hey there :) This is my second day as an ubuntu user :P

I had the same problem so I thought I could help a little.

I have Hardy by the way. My system is Turkish. So i wont be able to tell everything in english. 

Go to System -> Preferences -> Sound. and configure it like this:
here is a picture of my settings.

[[IMG]http://img175.imageshack.us/img175/5108/ekrangrntsdh8.th.png[/IMG]](http://img175.imageshack.us/my.php?image=ekrangrntsdh8.png)

First one: 1st option. which says something like "leave it to system to choose"
--------------------------------------------------------------------
Second one: the same with the first one.
--------------------------------------------------------------
Third one (play Sound) : ALSA advanced Linux sound "system??"

Forth one:(microphone) : ALSA advanced Linux sound "system??"
-----------------------------------------------------------------
Default mixer HDA Intel (Alsa mixer)  Yours may not be intel but it should be "alsa mixer"


Mine was "realtek OSS mixer" as the default mixer... That was the problem for me. when I fixed it, everything was fine with amsn.

---

