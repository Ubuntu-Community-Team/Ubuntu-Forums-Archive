---
title: "Nvidia GTX 650 TI BOOST: Too much red colour"
date: 2014-10-28
forum: General Help
---

### Post by Heroguy293 on 2014-10-28
Not exactly fixing a bug, but i need help to get rid of this weird graphical glitch. I have no idea where i'm supposed to post this, so forgive me if this is in the wrong Place.

[http://i1136.photobucket.com/albums/n492/Heroguy293/BL2bug_zpse3a86c16.png](http://i1136.photobucket.com/albums/n492/Heroguy293/BL2bug_zpse3a86c16.png)

[http://i1136.photobucket.com/albums/n492/Heroguy293/BL3bug_zps54ca0d6b.png](http://i1136.photobucket.com/albums/n492/Heroguy293/BL3bug_zps54ca0d6b.png)

Alright.. one of these pictures is me playing Borderlands 2. I Just installed the linux version of BL2 last night. I played it on WINE before. both versions have the same redness everywhere.

Since I had the same bug in wine and outside of WINE, so I figure that's not the culprit.

The second picture is me playing a beta version of runescape that uses HTML5 and has the same glitch.

Does anyone have any ideas on how to fix this? Because I have no clue what to do.

---

### Post by oldos2er on 2014-10-28
Moved to Gaming & Leisure.

Can you tell us what graphics card your system has, and whether you have proprietary drivers installed for it?

---

### Post by Heroguy293 on 2014-10-28
My graphics card is an Nvidia GTX 650 TI BOOST. i have no proprietary drivers installed. Would that fix it if I did?

EDIT: I just did some research, and I installed the proprietary drivers. No difference.

---

### Post by dannyboy79 on 2014-10-29
i know the exact reason this is happening to you. it happened to me also, i have a GTX 760 and I use the nvidia website driver 343.22 but if you installed the nvidia driver using ubuntu restricted drivers that's fine also.  run 
```
nvidia-settings
```
 and ensure that you uncheck everything within the Antialiasing Section

on a side note, next time try to make your thread title more precise because your current title is way to vague. ;)

---

### Post by mörgæs on 2014-10-29
> **dannyboy79 said:**
> 
Next time try to make your thread title more precise because your current title is way to vague.

Yes, please. Changed.

OP, does the red colour only appear while gaming?

---

### Post by dannyboy79 on 2014-10-29
i can for sure confirm this is due to having FXAA enabled within the nvidia-settings panel as well as texture sharpening. see here: [http://www.reddit.com/r/linux_gaming/comments/2i4ot1/borderlands_2_bug_weird_red_lines_in_shadows/](http://www.reddit.com/r/linux_gaming/comments/2i4ot1/borderlands_2_bug_weird_red_lines_in_shadows/)
and like I said, it happened to me. uncheck everything on the AA page of nvidia-settings and you should be golden.

---

### Post by Heroguy293 on 2014-10-29
Alright, I turned off the FXAA and now it's gone!

tyvm!

---

### Post by dannyboy79 on 2014-10-29
Don't forget to mark the thread solved using thread tools button near the top right side of your original post.

---

### Post by mörgæs on 2014-10-29
Not a gaming question, so moving into General Help for everyone to benefit from.
Yes, please remember the SOLVED thing.

---

