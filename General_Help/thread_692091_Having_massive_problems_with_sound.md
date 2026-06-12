---
title: "Having massive problems with sound"
date: 2008-02-09
forum: General Help
---

### Post by The happy panda on 2008-02-09
okay i installed Ubuntu fine then, I installed flash player (through the FF browser DONT DO) and the sound stopped, I tried everything including the alsa stuff and had NO luck what so ever.

Sound was fine on windows.

I got fed up and reinstalled it (kinda gave up and reformated the whole computer)
thought it would be back to where i started but NO sound still. 
Am SOOOOO confused at this!

:confused:

help please!

it works on windows tho!!!

---

### Post by forrestcupp on 2008-02-09
What alsa stuff did you try?  Did you try typing ```
alsamixer
``` in a terminal to make sure the volumes are turned up?

---

### Post by The happy panda on 2008-02-09
yup

not muted anything

I have drivers it reconises them

what did flash do to my sound?!?

I reinstalled alsa, checked i had drives, reinstalled drives. I know that when you reformat something the info doesnt go completely.

am so lost at this.

---

### Post by The happy panda on 2008-02-09
okay I figure the sound is being processed but not outputting for some reason

why would it not output to the speakers?

---

### Post by forrestcupp on 2008-02-09
If it started with Flash, you could try this. In Synaptic, go to Settings->Repositories. Click the Updates tab and check the boxes that say 'Pre-released Updates (gutsy-proposed)' and 'Unsupported Updates (gutsy-backports)'. Then click the reload button and see if there is an update for flashplugin-nonfree.

That gives you a newer version of Flash than what is in the official repos.  Maybe that will help.

---

### Post by The happy panda on 2008-02-09
yea i did that, i reinstalled flash, firefox, and alsa.

Something stopping the output  begin delivered to the speakers

---

### Post by The happy panda on 2008-02-09
I did a speaker test throught the terminal, 

Write error: -32,Broken pipe
Time per period = 3.028882
 0 - Front Left
Time per period = 2.986164
 0 - Front Left

this mean anything to anyone?

---

### Post by The happy panda on 2008-02-10
Okay I cheated, I used wine to emulate the sound from the windows part some how by accident :guitar:
go WINE!

---

