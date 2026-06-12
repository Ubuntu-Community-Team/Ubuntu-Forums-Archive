---
title: "XMMS freezes"
date: 2005-04-23
forum: General Help
---

### Post by Crimson Tide on 2005-04-23
I have sound on my system.  Used SPM to get XMMS.  It will open and run, but if I load up .mp3 into playlist or play single .mp3 XMMS will hang and I have to kill.

I also try to open .wav with XMMS and it will freeze then also.  I have re-installed XMMS and removed and re-installed XMMS.

Please help or help me find another mp3 player.

Thanks!

Did a test.  XMMS runs under KDE not Gnome....  Suggestions?

---

### Post by NeoChaosX on 2005-04-23
Preferences -> Audio I/O Plugins -> Output Plugin. Change to either ALSA or ESD, then try playing a song again.

---

### Post by bin on 2005-04-24
I've found that Beep Media Player set to esd works, but have had no luck with XMMS

---

### Post by LazyBoy on 2005-04-24
Once I had sound working  (Preferences -> Multimedia Systems Selector), and MP3s working elsewhere (rhythmbox), this got xmms working:

Start XMMS.  DO NOT hit Play or anything else that freezes it.
Open preferences, change the Output Plugin to eSound.
EXIT XMMS.

Start xmms again and play.

---

### Post by XDevHald on 2005-04-24
[QUOTE=LazyBoy]Once I had sound working (Preferences -> Multimedia Systems Selector), and MP3s working elsewhere (rhythmbox), this got xmms working:

Start XMMS.  DO NOT hit Play or anything else that freezes it.
Open preferences, change the Output Plugin to eSound.
EXIT XMMS.

Start xmms again and play.[/QUOTE]

Beautiful!! thanks LazyBoy!! worked like a charm :grin::grin: Been trying to get xmms fixed for a few weeks now :)

Thanks again my friend!

---

### Post by reid on 2005-04-26
[QUOTE=LazyBoy]Once I had sound working  (Preferences -> Multimedia Systems Selector), and MP3s working elsewhere (rhythmbox), this got xmms working:

Start XMMS.  DO NOT hit Play or anything else that freezes it.
Open preferences, change the Output Plugin to eSound.
EXIT XMMS.

Start xmms again and play.[/QUOTE]
 Thanks LazyBoy, that solved my problem!

---

### Post by DutchLau on 2005-04-26
You're a lifesaver LazyBoy, simple and effective! I changed it to ALSA so I could have multiple sounds  :)  Now I can finally scrap RealPlayer.. That bunch of %!@#$%#%

 :grin: 

Cheers mate

---

### Post by Leigh on 2005-04-26
Great tip, this worked for me also!

---

### Post by cdburgess75 on 2005-04-29
[QUOTE=Leigh]Great tip, this worked for me also![/QUOTE]
 me too

---

### Post by Curing@ on 2005-04-30
Thanks LazyBoy!!

 \\:D/

---

### Post by btdown on 2005-05-01
esd worked for me...thanks for the tip!

---

### Post by Poul on 2005-05-03
worked for me as well 
To think that at firsti wasted 30 minutes looking for mp3 plugin ;d

---

### Post by pdk001 on 2005-05-05
thanks lazyboy bunch for advice
it work as well now

---

