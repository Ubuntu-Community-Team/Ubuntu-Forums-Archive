---
title: "Flash &amp; Hardy - No sound"
date: 2008-04-30
forum: General Help
---

### Post by wadelewis4 on 2008-04-30
I've been working on Hardy for a week now, and just decided to mosey over to YouTube to check out some videos. Well, upon arrival of course I get the "plug-in needed" message, so I check Flash 9 and click install. It does it's thing and then the video started to play. One problem though... no sound. I gave a strange face and decided to try other videos to ensure it wasn't just that one. It's wasn't. No sound.

Any suggestions?
Anyone else having this issue?
:confused:

---

### Post by El Conquistador on 2008-04-30
yeah im having the same problem i just found out about it last night. after asking some fellow ubuntu users at school it turns out they all have the same issue. ive narrowed it down to the ubuntu itself as i first thought it was firefox (in a beta stage).

after looking at some other posts i noticed other people have the same issue, i saw some possible solutions but none worked for any of us (school buddies). im going to keep googling and ill post back if i find a solution.

---

### Post by wadelewis4 on 2008-04-30
> **El Conquistador said:**
> yeah im having the same problem i just found out about it last night. after asking some fellow ubuntu users at school it turns out they all have the same issue. ive narrowed it down to the ubuntu itself as i first thought it was firefox (in a beta stage).

after looking at some other posts i noticed other people have the same issue, i saw some possible solutions but none worked for any of us (school buddies). im going to keep googling and ill post back if i find a solution.

Thanks, I'm glad it's not just me.. lol. Hopefully we'll have a solution to this soon.

---

### Post by wadelewis4 on 2008-04-30
Okay, I just completely uninstalled firefox, and the flashplugin-nonfree, then reinstalled everything. Problem solved.

:guitar:

---

### Post by dvord on 2008-04-30
No such luck here.  Uninstalled and reinstalled but still no sound.

---

### Post by wadelewis4 on 2008-05-01
> **dvord said:**
> No such luck here.  Uninstalled and reinstalled but still no sound.

Try this link: [http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox]("http://markusthielmann.com/blog/defusing_one_most_annoying_bugs_ubuntu_hardy_heron_stop_flash_killing_firefox")

Scroll to the part that starts with **2) Alternative workaround**. 

*I left out the part about the nspluginwrapper, ehem. sorry!* 
Anywho, it worked so I'm spreading the joy. 

Good luck! :)

---

### Post by dvord on 2008-05-01
Didn't work for me unfortunately.

---

### Post by mister_k81 on 2008-05-01
Sounds like a problem with Flash and PulseAudio. Try installing libflashsupport to see if that helps... 

Type this into the Terminal; 

```
sudo apt-get libflashsupport
```

---

### Post by dvord on 2008-05-01
It was already installed.  

I think the X-Fi is working against me too.  There's another thread with others experiencing this:  

[http://ubuntuforums.org/showthread.php?p=4857546#post4857546](http://ubuntuforums.org/showthread.php?p=4857546#post4857546)

I did try uninstalling libflashsupport actually, based on some advice in that thread.

---

### Post by wadelewis4 on 2008-05-12
This isn't exactly on the same topic but I thought I would add it anyway: Sound in general. I have recently discovered that when I am listening to music (via rhythmbox or amarok) and I start another program that requires audio (e.g. a game or something) the sound system craps out. I have to restart to get sound working again. 

Until this is resolved I guess it'll become like second-nature and I'll have to retrain myself to multitask with sound.. lol.

---

