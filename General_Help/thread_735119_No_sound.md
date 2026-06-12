---
title: "No sound"
date: 2008-03-25
forum: General Help
---

### Post by ultraloveninja on 2008-03-25
So, I am not able to hear any sound out of my laptop when i do anything.  no audio playback, no system sounds, nada.

here is the output of aplay -l:

```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and when i go into the alsamixer, the master is maxed out and unmuted as well as the PCM too.
however, when i look at the mixer it says this:
 Card: HDA ATI SB                                                             &#9474;
&#9474; Chip: SigmaTel STAC9200                                                      &#9474;
&#9474; View: [Playback] Capture  All                                                &#9474;
&#9474; Item: Master [dB gain=0.00, 0.00]  

so i dunno.

i am not too sure what other settings there are that i can edit or look at.
any suggestions?

P.S.> I am running 7.10 on opengeu

---

### Post by superprash2003 on 2008-03-25
try this [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by ultraloveninja on 2008-03-25
well, i went through all the setting in my sound/volume properties and tested everything and got nothing but dead air.

any other suggestions?

am i missing a driver?

---

### Post by alejandro.mc on 2008-03-25
[http://ubuntuforums.org/showthread.php?t=724157](http://ubuntuforums.org/showthread.php?t=724157)

Try that. Sure you have searched all the Ubuntu Forums?

Good luck!

---

### Post by ultraloveninja on 2008-03-25
i followed that link and the website is not in english, but i did lend me to the idea of going into the syanptic package manager and look for some utils for alsa.
so i downloaded some other packages, but now it looks like that it's REALLY screwed up cause now it not recognizing anything.

and aplay -l comes back as this:

aplay: device_list:204: no soundcards found...


so, i'll have to go back and undo what i did,

any other suggestions?

---

### Post by ultraloveninja on 2008-03-25
ok.
looks like i totally jacked my audio.

now i really need help.

---

### Post by alejandro.mc on 2008-03-25
Go to ALSA's website and follow instructions to compile the newest ALSA drivers.

Good luck!

---

