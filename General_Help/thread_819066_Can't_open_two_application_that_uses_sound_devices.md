---
title: "Can't open two application that uses sound devices simultaneously"
date: 2008-06-05
forum: General Help
---

### Post by ayampanggang on 2008-06-05
Hello all,


I have a problem: i can't hear songs from two (or more) progs which uses sound devices.

For example, if i open youtube in my firefox while listening to musics with my rhythmbox, the youtube won't have any sounds. If the situation is reversed (e.g. i open rhythmbox while watching youtube) then rhythmbox won't have any sound. 

Same situation when i have my last.fm client open and then i fire rhythmbox, rhythmbox won't have sounds.

I dont remember having this problem in gutsy, while i can open my movie player while listening to rhythmbox, open youtube simultaneously, etc. Is there any fix for this?

Thank you very much :)

---

### Post by Plasma_NZ on 2008-06-05
Ok pritty simple fix this - had this before...

goto "menu - system - prefences - sound,  you'll have 3 tabs.. Device's, Sound, System-Beep, Goto the device's tab, change all device's there to alsa, then on the next tab "sound" - untick ESD.. problem solved... u may need logout and back in.. or restart the pc..

Hope this helps..

---

### Post by ayampanggang on 2008-06-05
wow that really works :)

any idea why is this happening? what did that ESD do? is this related to the new pulse audio driver in hardy?

thanks for the help

---

### Post by Plasma_NZ on 2008-06-05
> **ayampanggang said:**
> wow that really works :)

any idea why is this happening? what did that ESD do? is this related to the new pulse audio driver in hardy?

thanks for the help

Dont actually know, it was just something i noticed.. and havent looked back since.. :D far as i know it disabling ESD just stops the "themes sounds" ... your welcome :D

---

### Post by mrMango on 2008-06-05
ESD is a software sound mixing daemon, becuase many sound cards aren't able to do hardware mixing anymore. I have ESD enabled without losing my theme sounds.

Interestingly enough, it seems a lot of people are having issues with ESD being not enabled; you're the second person to ask that this morning.

---

### Post by Plasma_NZ on 2008-06-05
> **mrMango said:**
> ESD is a software sound mixing daemon, becuase many sound cards aren't able to do hardware mixing anymore. I have ESD enabled without losing my theme sounds.

Interestingly enough, it seems a lot of people are having issues with ESD being not enabled; you're the second person to ask that this morning.

What i was stating is that if u DISABLE ESD u wont have theme sounds...
And the software mixing enabled generally means u cant use the soud-engine in 2 applications that require it, from my observation..

---

### Post by mrMango on 2008-06-05
> **Plasma_NZ said:**
> What i was stating is that if u DISABLE ESD u wont have theme sounds...
And the software mixing enabled generally means u cant use the soud-engine in 2 applications that require it, from my observation..
Ah, I apologize for the misunderstanding.

---

