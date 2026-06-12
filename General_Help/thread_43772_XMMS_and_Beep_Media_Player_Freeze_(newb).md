---
title: "XMMS and Beep Media Player Freeze (newb)"
date: 2005-06-23
forum: General Help
---

### Post by Flakes on 2005-06-23
every time i try to play any kind of media (mp3, SHOUTcast, etc) on Beep Media Player or XMMS, both applications hang promptly at pushing the play button (the play button actually stays pushed in on the gui)... so i tried going out to Synaptic and removing everything that had to do with xmms and beep, reinstalled xmms only without any extra plugins and still, the same problem... can anybody help me?

---

### Post by Lunde on 2005-06-23
[QUOTE=Flakes]every time i try to play any kind of media (mp3, SHOUTcast, etc) on Beep Media Player or XMMS, both applications hang promptly at pushing the play button (the play button actually stays pushed in on the gui)... so i tried going out to Synaptic and removing everything that had to do with xmms and beep, reinstalled xmms only without any extra plugins and still, the same problem... can anybody help me?[/QUOTE]
 I had the same and I only had to change the sound device to Alsa and choose Alsa in XMMS preference.

Nice howto here for hearing multiple sounds in Ubuntu:
[http://www.ubuntuforums.org/showthread.php?t=32063](http://www.ubuntuforums.org/showthread.php?t=32063)

---

### Post by Flakes on 2005-06-23
i managed to go through the howto and changed everything... i still have sound, and have switched the output plugin to ALSA in xmms, but instead of freezing i get the "couldn't open audio" error... could it be my device? i'm using a C-Media PCI CMI8738-MC6

---

### Post by Kimm on 2005-06-23
make sure you dont have esd running in the backround.
Type:

killall esd

in the console and try again

---

### Post by Flakes on 2005-06-23
[QUOTE=Kimm]make sure you dont have esd running in the backround.
Type:

killall esd

in the console and try again[/QUOTE]
 that did it :) thanks a bunch

---

### Post by Kimm on 2005-06-23
no problem, glad to help ^^

---

