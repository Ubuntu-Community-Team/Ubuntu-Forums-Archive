---
title: "mouse/keybord stops workng"
date: 2007-10-03
forum: General Help
---

### Post by hessiess on 2007-10-03
p5n32-e sli mobo
q6600
gig ram
ubuntu feisty fawn, almost as default

the keyboard and or mouse sometimes stop working if the computer is left idle for 8 ish howers (overnight). its not masivly problematic, unless im downloading a large file or rendering something, i render stuff quite regulally.

any ideas?

---

### Post by Psyphre on 2008-05-26
a bit late i know, i had the same issues in the past, but there are 2 solutions:

1) go to bios, there should a section concerning legacy usb, you want to disable that. If your dual booting its a pain, cos your keyboard will not work in the grub selection menu (you have to enable it again if you want to select windows in grub).

2) a permanent solution, which i discovered by accident. Is to update your bios to the latest version. This completely solved it.

btw i have the same mobo as you, except its got "premium" at the end. If that makes a difference.

---

### Post by lisati on 2008-05-26
> **hessiess said:**
> p5n32-e sli mobo
q6600
gig ram
ubuntu feisty fawn, almost as default

the keyboard and or mouse sometimes stop working if the computer is left idle for 8 ish howers (overnight). its not masivly problematic, unless im downloading a large file or rendering something, i render stuff quite regulally.

any ideas?
I use Feisty too: I had a problem with a USB mouse and a USB keyboard locking up after a few minutes (not hours) on my laptop. The solution I used is described in this thread: [http://ubuntuforums.org/showthread.php?t=560991]("http://ubuntuforums.org/showthread.php?t=560991")
***Note: the above applies to *USB* input devices***
> **Psyphre said:**
> 
2) a permanent solution, which i discovered by accident. Is to update your bios to the latest version. This completely solved it.

Thanks for that - I recently updated the BIOS on my laptop; I'm doing a fresh install on my laptop to fix a couple of muck-ups and will see what happens.

Have a great day, everyone, and I hope the ideas help.


EDIT: NOTE: The particular mouse/keyboard problems I was having were different to those described by the OP, and the soloution I proposed might not necessarily help. Sorry about that. 
EDIT: Note 2: I just did a clean install on my laptop with an updated BIOS and discovered that I still had to apply the "tweaks" that I'd used before.

---

