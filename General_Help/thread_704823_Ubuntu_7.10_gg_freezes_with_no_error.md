---
title: "Ubuntu 7.10 gg freezes with no error?"
date: 2008-02-22
forum: General Help
---

### Post by teryowen on 2008-02-22
I recently used one of my computers which i haven't used in a month and when i used the computer it froze, for no reason at least it didn't give a reason prior to the freezing CPU usage levels are fine (i have an indicator in my tool bar)

So it freezes and it gives no error, any idea what the problem could be or where could i find the error log?

---

### Post by Crafty Kisses on 2008-02-22
> **teryowen said:**
> I recently used one of my computers which i haven't used in a month and when i used the computer it froze, for no reason at least it didn't give a reason prior to the freezing CPU usage levels are fine (i have an indicator in my tool bar)

So it freezes and it gives no error, any idea what the problem could be or where could i find the error log?

Have you checked all your logs?

---

### Post by teryowen on 2008-02-22
No I havnt checked a single one, because i dont know where they are or which one to look at.

---

### Post by photismos on 2008-02-22
I'm very new to Linux, but I was having very similar errors to what you describe....freezing but still able to use my mouse, although to no avail since nothing was selectable, and of course the keyboard was completely useless (frozen)...nothing worked.  It was happening intermittently, wondered if it was Firefox or my movie player or something I was doing...not so though.  

I searched a few threads here and found that editing "/boot/grub/menu.lst" adding just two little words..."noapic nolapic" fixed it completely.  Since then I've had no freezes at all.

Here's where the those "words" went in the context of my menu.lst, if it helps you to know where to put it:  

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=56ef75eb-5ce9-4863-a4ee-2d4d2a167847 ro noapic nolapic quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

...AND that's it.  you put it in that "kernel" line and restart.  Hope it helps.  If it does, would be nice if you confirmed that for others having the same problem... =)  That's what I'm doing...trying to find the original thread I found this solution in to confirm it works!  =D  ...well, again...hope it helps!

---

### Post by teryowen on 2008-02-22
Alright what you describe is correct it freezes mouth still works but no selections. So i tried the line during boot and now editted to the menu.lst file in /boot/grub/ and so far so good.

Ill edit this post in 20minutes or so to let you know if its still fine or if it doesnt work.

---

### Post by teryowen on 2008-02-22
Yap everything is still working fine, so great thank you for the post. Dont really understand the problem but hey its a solution.

---

