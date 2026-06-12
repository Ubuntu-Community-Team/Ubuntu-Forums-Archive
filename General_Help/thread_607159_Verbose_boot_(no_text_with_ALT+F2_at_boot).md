---
title: "Verbose boot (no text with ALT+F2 at boot)"
date: 2007-11-08
forum: General Help
---

### Post by AkumA on 2007-11-08
Hi.. i've updated to Gutsy and now i'm becoming crazy because ALT+F2 doesn't show me any information about the boot.
Just yesterday evening i became really angry: i've installed another linux distribution along Ubuntu Gutsy and Windows and, when i tried to load Ubuntu, i got black screen.

That's fine if it's doing fsck.. but at that point i've waited too long without knowing what was going on.

After that i've used old 2.6.20 Feisty Kernel and i saw tons of problems about UUID and other stuff, and i was able to fix those problems somehow..

I've read somewhere that Gutsy has this by default but honestly i need to know what's happening when i boot my PC..
If i was a really unexperienced user i think i would be playin' with Windows right now, or other distribution after a nice format to Ubuntu's partition.

I have black screen, what am i supposed to do?
This is NOT usable..

What if i hadn't old Feisty kernel?

Is there a way to fix it!?

I've search around (both forum and google) about "verbose boot" but i haven't found anything useful at first sight..


Could someone help me!?

---

### Post by logos34 on 2007-11-08
on the grub menu screen highlight gutsy and hit 'e' to edit.  Take out 'quiet' option at end of kernel line

---

### Post by AkumA on 2007-11-08
> **logos34 said:**
> on the grub menu screen highlight gutsy and hit 'e' to edit.  Take out 'quiet' option at end of kernel line

I've already done that.. i obtain orange text under Usplash..
Fsck controls and other stuff (like "insert root password for manteinance" can be monitored with that?)
Is it the same of "ALT+F2"  (switch to runlevel 2) option?

---

### Post by logos34 on 2007-11-08
try adding **debug** option (or **BOOT_DEBUG=2**)

or else select the gutsy recovery kernel

---

### Post by AkumA on 2007-11-29
> **logos34 said:**
> try adding **debug** option (or **BOOT_DEBUG=2**)

or else select the gutsy recovery kernel


Resolved:

[http://kubuntuforums.net/forums/index.php?topic=3087749.msg94991#msg94991](http://kubuntuforums.net/forums/index.php?topic=3087749.msg94991#msg94991)

...fortunately... now it's much better

---

