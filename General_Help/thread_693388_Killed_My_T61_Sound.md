---
title: "Killed My T61 Sound"
date: 2008-02-11
forum: General Help
---

### Post by Merciless on 2008-02-11
I recently installed Ubuntu on a new T61 laptop.  After customizing it to my liking I mistakenly killed my sound... And I can't figure out how i managed to do it. So... crap :(. 

It was working before I tried to get totem working with DVDs, installed powertop, and before I installed "Thinkfinger."  I removed Thinkfinger hoping that might be the problem.

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

The error message from "Sound Preferences" is "gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open resource for writing"

---

### Post by neurostu on 2008-02-11
consult [www.thinkwiki.org](www.thinkwiki.org) they are pretty much devoted to getting linux working on thinkpads and have resolved a lot of the issues.

---

### Post by Merciless on 2008-02-11
Thanks, the answer was there.

For completeness:
The problem was if you disable the modem in the bios the sound quits working.  Renabling the modem fixed the problem. 

[http://www.thinkwiki.org/wiki/Problem_with_no_sound_on_ThinkPad_R60e](http://www.thinkwiki.org/wiki/Problem_with_no_sound_on_ThinkPad_R60e)


Thanks neurostu!

---

