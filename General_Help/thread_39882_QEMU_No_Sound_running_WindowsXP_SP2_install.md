---
title: "QEMU: No Sound running WindowsXP SP2 install"
date: 2005-06-06
forum: General Help
---

### Post by kinkadius on 2005-06-06
i just finished installing QEMU (with KQEMU support) and i must admit it rocks. however one problem i'm running into is that even though i use "-enable-audio" when running it. 

I can think of two things that may provide a clue to this:

1) upon "./configure" i noticed that "FMOD" was listed as a no. i know that FMOD is sound support, but in the HOWTOs i've read for installing QEMU, they said nothing of FMOD.

2) i did not use "-enable-audio" when installing Windows XP SP2 (SP2 is slipstreamed into the cd). Should i have used that for detection? you would think though that windows would supposedly find and install the virtual sound card if you use "-enable-audio"


granted i'm sure there's some piece of information that i'm not providing which may  help out, but i can't think of any (dramatic irony) :-D

Any Ideas? anything information i can provide?

---

### Post by ayates on 2005-06-11
I had to  add a SB16 card through XP 'Add/Remove Hardware'.

---

