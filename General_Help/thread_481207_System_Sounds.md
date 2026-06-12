---
title: "System Sounds"
date: 2007-06-22
forum: General Help
---

### Post by strange_cathect on 2007-06-22
I have a weird issue:

My sound card is working fine: I can listen to my music and have audio when I play video, CDs, etc.

However, my system sounds have disappeared.  When I go into Control Center | Sounds and try to play the sounds that are selected for a sound event, nothing happens.  In fact, the only system sound that works is the little drum beat at the login window.  After Ubuntu loads, all other system sounds do not play.

I attempted to select a new sound for a system event.  But these sounds are unplayable in the sound selector too.

Any ideas?

---

### Post by r0ck80y on 2007-06-22
Even my system sounds weren't working. So i went to System-> Preferences -> Sound
In the Sound tab, 'Enable software sound mixing (ESD)' and 'Play system sounds'. Then in the list below choose the sounds you want to be played for the various actions. Then logout and login again. Your sounds should be enabled :)

---

### Post by strange_cathect on 2007-06-22
Yes,  I tried that already.

Problem is when I try to play the sounds there is nothing....silence and tumbleweeds.  This is true even in the system sound selection that you describe in your response.

Any other ideas?  How could this happen.  All sound works perfectly EXCEPT for system sound events.

---

### Post by NeoLithium on 2007-06-22
I know with my sound card, for some reason there's an adjustment that mutes the system sounds, but music will still play.  run the command ```
alsamixer
``` in a terminal and see if anything is turned down or muted that may help?

---

### Post by strange_cathect on 2007-06-23
All green; no mutes.

---

