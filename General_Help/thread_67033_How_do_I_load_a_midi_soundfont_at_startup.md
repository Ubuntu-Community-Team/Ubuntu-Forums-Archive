---
title: "How do I load a midi soundfont at startup?"
date: 2005-09-19
forum: General Help
---

### Post by oliwally on 2005-09-19
I am trying to use kmid to play a midi file. However, it doesn't work until I do a "sfxload mysoundfont.SF2". After that, all is well until I restart my computer.

How can I have my soundfont load at startup? 

The only way I have managed to do this is to create a new "link to application" which executes the sfxload, then sticking this into the Autostart folder (I'm using KDE). But this seems a bit slow and cumbersome.

I have also tried to look at other postings on this forum: [www.ubuntuforums.org/showthread.php?t=47409&highlight=sfxload](www.ubuntuforums.org/showthread.php?t=47409&highlight=sfxload)
which told me to do the following:
> Just create a file "/etc/modprobe.d/soundfont" and put
in it:
post-install snd-synth-emu10k1 /usr/bin/asfxload /path/to/my/soundfont.SF2

But this did not work for me either. 

Please help. (I'm using a creative SB Live soundcard if that helps.)

---

### Post by oliwally on 2005-09-20
bump

---

### Post by oliwally on 2005-09-21
Some help pleeeeeease. :roll:

---

### Post by oliwally on 2005-09-23
bump

---

### Post by oliwally on 2005-09-24
starting to get some help in a different thread now:

[http://www.ubuntuforums.org/showthread.php?t=47409&highlight=sfxload](http://www.ubuntuforums.org/showthread.php?t=47409&highlight=sfxload)

Thanks folks

---

### Post by oliwally on 2005-10-05
> starting to get some help in a different thread now:

[http://www.ubuntuforums.org/showthre...hlight=sfxload](http://www.ubuntuforums.org/showthre...hlight=sfxload)

Thanks folks

Hmmm.... despite many different suggestions, it appears that all that help still didn't solve my problem on how to get midi soundfonts loaded from startup. Does anyone have a sure way of achieving this? Would love some help.

---

