---
title: "Can't access folders on mounted drive..."
date: 2007-05-04
forum: General Help
---

### Post by brodiepearce on 2007-05-04
Hellooo,

I've only started experiencing this problem after reinstalling Feisty.  In my standard user profile, the folders on one of my hard drives come up as blank files, and I cannot access them or expand them.  If I double-click them it says "Couldn't display "folder".  The attempt to log in failed.".

However, if I browse to it through sudo nautilus, the folders come up fine, however the drives themselves do not come up in root's sidebar in nautilus, and you have to get to them through the /media folder.

No matter how many times I reinstall this, nothing changes, the only thing I can think of that may have had an effect is that I changed the permissions of everything in my home folder to my user profile, which is what prompted the first reinstall, after which I have these problems.  (Note that I have been doing a format on all system drives for every reinstall).

I cannot find any other threads describing these issues, hopefully it's not too uncommon.  Cheers in advance for any help.

*edit*
**Problem Solvered, a friend on IRC got me to set proper drive permissions and ownership through terminal.**

---

