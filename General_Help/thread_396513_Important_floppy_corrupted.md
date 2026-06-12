---
title: "Important floppy corrupted"
date: 2007-03-29
forum: General Help
---

### Post by Biochem on 2007-03-29
A friend of mind has a floppy disk with important data on it and it is corrupted. When he put it in win XP it says the disk is not formated. I was thinking maybe fsck might do the trick but I don't know how to use it.

I would greatly appreciate any halp on this one
Thank you

---

### Post by hde on 2007-03-30
Hi, I assume the floppy contains a fat system and has been used under windows. There exists several freely available undelete tools for windows, I suggest you or your friend could try some of them. I can't give advice on which is best, but a search on google wil give you many hits.

If you want to take a snapshot of the floppy, in case it is deteriorating, you can do it under ubuntu which a command like this

dd if=/dev/fd0 of=imageoffloppy.img

alternatively you can use GNU ddrescue (in package gddrescue) which should handle read errors better.

Tools you can use under ubuntu for rescuing files are ex. foremost and magicrescue (both in ubuntu). I have never used those programs, so I can not say more about them.

good luck

---

### Post by Biochem on 2007-03-31
Thanks for your help hde. I tried foremost but was still unsuccessful the floppy must have been more screwed up than I though :cry:

---

