---
title: "[SOLVED] Sound stopped working after reboot"
date: 2007-11-02
forum: General Help
---

### Post by NoSmokingBandit on 2007-11-02
Everything was working fine, then i shut my computer down last night when i went to bed but when i tried listening to music today i got no sound. Everything else works as usual, but for some reason i have no sound at all from exaile, totem, or firefox. Im not sure what i could have dont to have this happen. Last time i couldnt get it fixed so i got pissed of and reinstalled gusty, but im on my 3rd install due to stuff just not working consistently and i really dont want to have to go through the re-install thing again.

---

### Post by NoSmokingBandit on 2007-11-03
Screw it, if nobody can help me fix it ill have to re-install gusty (again)...

---

### Post by NoSmokingBandit on 2007-11-03
Ok, so i reinstalled gusty (again...) and everything was working fine. Then i installed audacity to record some stuff. Now i have no sound again. I went to synaptic and chose to completely uninstall audacity but i still have no sound. Anyone at all know what keeps doing this?

---

### Post by Qaowuon on 2007-11-03
i have a somehwat similair problem, one moment the sound was working great and all and after a reboot i had absolutely no sound, no system sound nothing.

---

### Post by NoSmokingBandit on 2007-11-03
i have a beep from the internal speaker if i hit backspace too many times during login, but other than that i have pure silence.
Its good to know im not alone though ;)

---

### Post by BeardlessForeigner on 2007-11-04
I'll post in here for solidarity of the soundless...I actually lost sound without even rebooting, all I did that I can think of is install gpodder. I am contemplating reinstalling but I'm reluctant if sound will just stop working after another update. System beep is still working.

edit: my PCM in volume control was muted >_<

---

### Post by NoSmokingBandit on 2007-11-04
ARGH! Gusty is quite frankly pissing me off. I rebooted in to ubuntu hoping that someone would have answered my post and i could fix my sound problem but now my resolution is stuck at 640x480/50hz. I cant change it back to the 1280x1024 i usually have, or to anything else at all.

---

### Post by NoSmokingBandit on 2007-11-05
so out of the thousands of people here nobody knows/cares enough to help?

---

### Post by brianbarry on 2007-11-05
Make sure PCM level is on in the mixer settings.  I've also needed to re-install alsa in the past to get sound working.  I hope this helps.

Brian

---

### Post by YoshiHNS on 2007-11-05
how did you reinstall alsa. I tried that through the sys package manager and it did not work.

---

### Post by NoSmokingBandit on 2007-11-05
> **brianbarry said:**
> Make sure PCM level is on in the mixer settings.  I've also needed to re-install alsa in the past to get sound working.  I hope this helps.

Brian

I rebooted into ubuntu and now my resolution is back to normal :confused::confused:
Anywho, i reinstalled the alsa package through synaptic but it didnt help anything. I'll try a complete removal then re-install in a minute and let you know what happens.

Edit:
nvm, if i want to completely uninstall alsa i nee to lose the ubuntu-minimal package with it and that looks like something id like to keep on there in case **** goes wrong before i reinstall alsa.

Edit 2:
I installed the alsamixer gui package and ran it to see that the card was set to my integrated audio card. I cant seem to get it to change to my sblive card though, anyone know how to change that?

---

### Post by NoSmokingBandit on 2007-11-05
I fixed it myself! GO ME! Lol, ill write down how i did it for everyone here. I have both integrated and pci audiocards so when i installed audacity it must have screwed up what card was the default. Anyway, this is the way i fixed that:
1 Install the package "asoundconf-gtk" in synaptic.
2 Hit Alt+F2 and run the command "asoundconf-gtk"
3 Choose whatever soundcard you use
4 Fin.

---

### Post by rykel on 2007-11-05
I am also facing the 3 major problems mentioned here:

[LIST=1]
[*]No sound - NEVER had sound been a problem since Warty Warthog for me...
[*]Low resolution upon every reboot
[*]Hardcore freezing when downloading lots of data (eg. via bittorrent)
[/LIST]

---

### Post by drs305 on 2007-11-05
> **rykel said:**
> I am also facing the 3 major problems mentioned here:

[LIST=1]
[*]No sound - NEVER had sound been a problem since Warty Warthog for me...
[*]Low resolution upon every reboot
[*]Hardcore freezing when downloading lots of data (eg. via bittorrent)
[/LIST]

rykel,

Since this thread has been marked SOLVED and you have additional problems not mentioned in this thread title, you will have more success if you open a new thread to deal with these issues.

Good luck.

---

### Post by NoSmokingBandit on 2007-11-05
yeah, sorry dude, but im dont with this thread now so i dont think alot of people will be looking at it.

---

### Post by rykel on 2007-11-05
oops, sorrie buds... will do, thanks!!

---

