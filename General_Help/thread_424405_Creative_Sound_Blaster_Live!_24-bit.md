---
title: "Creative Sound Blaster Live! 24-bit"
date: 2007-04-26
forum: General Help
---

### Post by Chestnux38 on 2007-04-26
For a while i've been searching all over the net to get my sound card working on Ubuntu and I can't find anything to help. I'm currently using my motherboard soundcard but only 2 of my speakers work. I want all of my 5 speakers to work. Is their anyway to get the Creative Sound Blaster Live! 24-bit soundcard to work?

---

### Post by sevencapitalsins on 2007-04-26
Hi,

I think your problem may be solved following this post:

[How to get your SB Live! work with Ubuntu to the fullest]("http://ubuntuforums.org/showthread.php?t=161817")

Byez
Luca

---

### Post by Chestnux38 on 2007-04-26
It really doesnt help with anything

---

### Post by sevencapitalsins on 2007-04-26
I have an Audigy2, and for now it works: but sometimes I see that the selected sound card is the on-board Intel ICH5...

When you open alsamixer, what card does it set? the sound balster one or the on-board one?

Bye
Luca

---

### Post by Chestnux38 on 2007-04-26
Ca0106

---

### Post by sevencapitalsins on 2007-04-26
[http://ubuntuforums.org/showthread.php?t=19307](http://ubuntuforums.org/showthread.php?t=19307) This one?

---

### Post by Chestnux38 on 2007-04-26
Still doesnt work. :(

---

### Post by Chestnux38 on 2007-04-26
Bump! I really need this fixed.

---

### Post by brenx on 2007-05-07
same problem here.

---

### Post by cerda on 2007-05-08
i have the same problem here

---

### Post by strabes on 2007-05-08
Sorry for the non answer but next time you guys buy 5.1 speakers make sure they have a Dolby Digital Pro Logic II decoder. It decodes a stereo track and plays it through all 5 speakers and the woofer.

---

### Post by sevencapitalsins on 2007-08-26
I solved the problem when it came to me in Feisty: suddenly my  audigy soundcard stopped to work.

 Maybe it is because the soundcard integrated in your mobo is the first choice picked by ALSA so the sound blaster Live!  is deactivated. You just have to set your preferences about wch soundcard must be the first one.


[http://alsa.opensrc.org/index.php/MultipleCards#How_to_choose_a_particular_order_for_multiple_installed_cards]("http://alsa.opensrc.org/index.php/MultipleCards#How_to_choose_a_particular_order_for_multiple_installed_cards")

@Strabes: you don't have to do it to get 5.1 sound out of a 5.1 card.

---

### Post by expatCM on 2007-08-26
My solution was to replace the card.   I worked on finding a solution for months and replacing the card was the only effective way forward I could find.  I was VERY disappointed with this but I had to face reality.

It seems that in general terms it is best to steer well clear of Creative products until they decide to show a little support for Linux ...  at present they are only interested in the Windows market and not releasing any information which would let you help yourself ................  Some Creative sound products will work well but most either do not work at all or only partially work.

---

### Post by Jeremy_Wlk on 2007-10-26
Hi! I have 2.0 speakers and my Sound Blaster 24-bit works properly (at least as it seems to me, heh) but there are still a few little problems to deal with:

1) [SOLVED] Can't control volume through Volume Applet.

2) Because of some unknown reason the greeting and farewell sounds in Ubuntu (Feisty) don't play every time I enter or exit OS. Say once per three-four times.

Perhaps, the reason is concealed in Sound Preferences? They are:
```

Sound events: CA0106
Music and Movies: CA0106
Audio Conferencing: CA0106
Default Mixer Tracks: **Intel82801DB-ICH4** (Alsa-mixer)
```

---

