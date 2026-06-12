---
title: "No sound with TVTime"
date: 2005-07-21
forum: General Help
---

### Post by Boopop on 2005-07-21
I've got an Aver TVStudio card, with its audio out plugged in to the line in on my sound card. I get no sound but i do get a picture. I've got the volume on full, and i have checked the mixer for anything that's muted.

When i put tvtime on. all I hear is a odd buzz noise when i move the mouse or anything else happens on the screen.

thanks in advance, Boopop

---

### Post by bdamon on 2005-07-21
[QUOTE=Boopop] I've got the volume on full, and i have checked the mixer for anything that's muted.

[/QUOTE]

What mixer did you use? For my TV card I found I had to go into alsamixer from a cli and mess with it until I found the right setting that controled the input source. After I had it set I ran alsactl store to save the settings.

---

### Post by Boopop on 2005-07-21
[QUOTE=bdamon]What mixer did you use? For my TV card I found I had to go into alsamixer from a cli and mess with it until I found the right setting that controled the input source. After I had it set I ran alsactl store to save the settings.[/QUOTE]

How do I do that?

---

### Post by Boopop on 2005-07-22
Anybody?

---

### Post by bdamon on 2005-07-22
This is what I did.

You can have tvtime open while you are doing this and you should hear sound when you get the right line set. Make sure in tvtime you have the volume adjusted up some using the Left/Right arrow keys as I believe by default the first time you run it the volume is at 0.

 Open a terminal and type in  sudo alsamixer  use the Left/Right arrow keys to navigate and the Up/Down arrow keys adjust the volume and the m key to mute/unmute.  Once you get sound in tvtime hit the escape key to exit. When you have everything working then you can type in the terminal   sudo alsactl store   to save your settings.

---

### Post by slada on 2005-07-30
[QUOTE=Boopop]I've got an Aver TVStudio card, with its audio out plugged in to the line in on my sound card. I get no sound but i do get a picture. I've got the volume on full, and i have checked the mixer for anything that's muted.

When i put tvtime on. all I hear is a odd buzz noise when i move the mouse or anything else happens on the screen.

thanks in advance, Boopop[/QUOTE]
 I have an AverTV card and got the sound to work by rightclicking on the volume control on the top panel (add the object to the panel if it is not there) and choosing "open volume control."  I had to increase the 'line-in" volume and I had sound.

Hope it works.

---

### Post by TreeFrog on 2005-08-10
[QUOTE=bdamon]This is what I did.

You can have tvtime open while you are doing this and you should hear sound when you get the right line set. Make sure in tvtime you have the volume adjusted up some using the Left/Right arrow keys as I believe by default the first time you run it the volume is at 0.

 Open a terminal and type in  sudo alsamixer  use the Left/Right arrow keys to navigate and the Up/Down arrow keys adjust the volume and the m key to mute/unmute.  Once you get sound in tvtime hit the escape key to exit. When you have everything working then you can type in the terminal   sudo alsactl store   to save your settings.[/QUOTE]

For my setup it was the AUX setting in alsamixer that needed changing.

enjoy.

---

### Post by dcarpenter on 2005-10-10
[QUOTE=bdamon]This is what I did.

You can have tvtime open while you are doing this and you should hear sound when you get the right line set. Make sure in tvtime you have the volume adjusted up some using the Left/Right arrow keys as I believe by default the first time you run it the volume is at 0.

 Open a terminal and type in  sudo alsamixer  use the Left/Right arrow keys to navigate and the Up/Down arrow keys adjust the volume and the m key to mute/unmute.  Once you get sound in tvtime hit the escape key to exit. When you have everything working then you can type in the terminal   sudo alsactl store   to save your settings.[/QUOTE]

Thank you very much kind sir :)  
Tv Time was giving me a headache for almost 2 hours while I fought with my volume controls.. this tip got sound working in about 10 seconds :rolleyes:   

The audigy 2 has a volume control called Audigy Analog that I had to turn up to get sound.

---

### Post by drphilngood on 2006-11-12
This just helped me to fix my problem but I had to search a loooooong time to find it.  Therefore, I figured I'd give it a bump to help all the others I noticed along the way with the same problem.:D

edit:
This worked for me with an Audigy 2 Platinum with WinFast's TV2000 XP Series Model 3

---

