---
title: "Weird VMware problem"
date: 2007-11-05
forum: General Help
---

### Post by highstead on 2007-11-05
Sorry, not sure what subject this belongs under... so i went with general.

Alright so i have my VMware installed running smoothly.  Everything looks good to go.  Except when i run 'rdesktop -A -s 'c:\seamelessdrpshell...' (seamlessdrpshell with remote desktoping)  things get 'weird'.

If i run VMware through the traditional GUI it works fine i can type and do whatever as expected.  When i however move to the ubuntu/windows shell my keyboard gets 'freaky' with me.  
- When i'm in notepad, things run smoothly as expected
- the keyboard is set to U.S. English - Dvorak  (this is the intended keyboard layout)
- If i hit windows+key 'r' Ubuntu zooms in?? and moves my cursor to between my 2 monitors or effectivly to the 'center' of the screen.  (only happens with VM ware/rdesktop open)
- in the run window, instead of home row looking like a typical dvorak layout (aoeuidhtns-) it looks like: ar.gcedybo[

---

### Post by highstead on 2007-11-06
Hmm, it seems when i run the VMware server console everything runs fine.  However when i run it through rdesktop -A theres problems.  I attribute this to the way the keyboards are handled.  When the VMware 'windows' was set to US-English  (non-dvorak) it functioned fine.  Presumably the keyboard is handled in such a matter that the keys are 're-evaluated'.  

So, Would this be a bug of VMware, rdesktop, or Ubuntu? and how would one submit it?

---

### Post by fjgaude on 2007-11-06
Have you installed the VMware Tools from the VM tab in the vm window? Such provides much of the speed that VMware has.

---

