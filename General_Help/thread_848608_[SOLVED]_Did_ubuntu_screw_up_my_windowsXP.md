---
title: "[SOLVED] Did ubuntu screw up my windowsXP?"
date: 2008-07-03
forum: General Help
---

### Post by esbo on 2008-07-03
My XP has been screwed up recently, Ubuntu is on the list of suspects.
Symptoms include very long boot up, sluggish performance, sticky mouse
pointer, stuttering music.
 I have no backup as such except the system recovery 'thing'
What does the install do (7.0.4 IIRC)
I night have to try uninstalling.

---

### Post by mister_pink on 2008-07-03
The only possible thing the ubuntu installation could have done to XP is leave it with not enough disk space. This could cause some of those symptoms. Boot into XP and see what you've got left on your c drive.

---

### Post by PinkFloyd102489 on 2008-07-03
Sounds like you've cramped XP in a box. How much RAM do you have in the machine?

---

### Post by Elfy on 2008-07-03
Is this the wubi install you did the other day?

---

### Post by |{urse on 2008-07-03
Agreed, all of the things you mentioned earlier are indicative af a pagefile in distress. Try freeing up some room or uninstall XP (it runs better when it isn't installed). If you're afraid of using Ubuntu as your primary OS, don't be, everyone here will help you if you need it. Unless you're a hardcore 3d gamer you don't really need it anyways.

---

### Post by esbo on 2008-07-03
> **forestpixie said:**
> Is this the wubi install you did the other day?

Yes.
I am going to uninstall it and see what happens.

Where is the bit which gives you the menu to choose the operating system at startup?

---

### Post by esbo on 2008-07-03
This is my boot.ini:-
===============
[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home 
Edition" /fastdetect /NoExecute=OptOut
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
c:\wubildr.mbr="Ubuntu"
====================

Incidently Ubuntu is on drive f: not c:

---

### Post by Elfy on 2008-07-03
No idea I'm afraid as I don't have windows to try it on.

But it could make a difference to the way they interact.

---

### Post by p_quarles on 2008-07-03
Moved to the Wubi section.

---

### Post by tjwoosta on 2008-07-03
better off with a regular dual boot

---

### Post by esbo on 2008-07-03
I  have uninstalled it now.
Made no difference, still slow.
I guess I might as well put it back on.

Incidently it worked very well, very fast, quick boot, no stuttering.
I will reinstall it now.

I guess I have a huge incentive to migrate now, very hard to play music
on XP without stuttering.

---

### Post by cariboo on 2008-07-03
XP boots off of the first drive no matter what partition or disk it or any other operating system are actually on.

Jim

---

### Post by esbo on 2008-07-04
My humble apologies to the Ubuntu Community.

It was *all* microshytes fault. (B*stards) :lolflag:

Will tell you about it later (DMA  PIO thing)

---

### Post by ago on 2008-07-04
Would be good to post more details as it might be useful to other users in the same situation.

---

