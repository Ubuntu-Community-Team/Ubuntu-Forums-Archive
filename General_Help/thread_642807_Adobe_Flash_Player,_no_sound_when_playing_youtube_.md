---
title: "Adobe Flash Player, no sound when playing youtube video"
date: 2007-12-17
forum: General Help
---

### Post by kenan6346 on 2007-12-17
I've installed Adobe Flash Player 9 and now I can play videos on YouTube, but I'm not getting any sound. I've looked at the other threads (these ones: [link](http://ubuntuforums.org/showthread.php?t=556907) [link2](http://ubuntuforums.org/showthread.php?t=214674) [link3](http://ubuntuforums.org/showthread.php?t=321048&highlight=firefox+no+sound)), I've done "sudo apt-get install alsa-oss", and tried to edit "/etc/firefox/firefoxrc", but there isn't anything in that file to edit; its there but there's nothing in it. 

Can someone give me a hand? I've got Ubuntu 7.10.
Cheers

---

### Post by kenan6346 on 2007-12-18
nudge?

---

### Post by grahambo2005 on 2007-12-18
Hey

Is your sound card working at all? IE can you listen to music in a media player?

Graham

---

### Post by kenan6346 on 2007-12-18
Yea I can listen in my media player, also the sound is working now so I think it may have just been a restart of the computer or something, thanks anyway ;)

---

### Post by P.tritas on 2007-12-22
Got the same issue. My nerves!

---

### Post by TidusBlade on 2007-12-22
It might have something to do with OSS and ALSA, since I installed OSS, ALSA got removed and youtube videos arent working properly...

---

### Post by DarkN00b on 2007-12-29
I just fixed this problem on my laptop by following the instructions [here]("http://www.arsgeek.com/?p=2966"). It takes literally a few seconds to fix this. I had to make sure Firefox was open when I installed it though. The installer would crash if Firefox wasn't open.

---

### Post by flashm on 2008-02-22
I have the same issue, but on 64 bit Gutsy. That package is for 32 bit. 

Anybody got any suggestions?

---

### Post by ubuntu-freak on 2008-02-22
> **kenan6346 said:**
> I've installed Adobe Flash Player 9 and now I can play videos on YouTube, but I'm not getting any sound. I've looked at the other threads (these ones: [link](http://ubuntuforums.org/showthread.php?t=556907) [link2](http://ubuntuforums.org/showthread.php?t=214674) [link3](http://ubuntuforums.org/showthread.php?t=321048&highlight=firefox+no+sound)), I've done "sudo apt-get install alsa-oss", and tried to edit "/etc/firefox/firefoxrc", but there isn't anything in that file to edit; its there but there's nothing in it. 

Can someone give me a hand? I've got Ubuntu 7.10.
Cheers

 
Does adding the lines not work though? It's still an instruction to Firefox. Strange how it's empty though. Any with a similar name? Or delete the empty file and reinstall FF.
 
Nathan
 
P.S. Incase anyone else needs it, troubleshooting section of my how-to includes the standard fix for flash with no sound.

---

### Post by oxxxid on 2008-04-25
The package is available on Synaptic. Just search for 'libflashsupport' and you're done!

---

### Post by andre.franciosi on 2008-05-04
Just install libflashsupport ['apt-get install libflashsupport' or search for it on Synaptic] and restart Firefox. This will solve it. It's always better to use original repositories instead of download and install .deb files.

afr

---

### Post by ubuntu-freak on 2008-05-05
> **oxxxid said:**
> The package is available on Synaptic. Just search for 'libflashsupport' and you're done!

The question was regarding Gutsy, strange how you responded to it the way you did.

Nathan

---

