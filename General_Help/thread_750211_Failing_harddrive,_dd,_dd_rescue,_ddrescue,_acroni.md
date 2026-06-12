---
title: "Failing harddrive, dd, dd_rescue, ddrescue, acronis true image: not happy"
date: 2008-04-09
forum: General Help
---

### Post by tjbo1m on 2008-04-09
Ok, obviously I registered here to ask this question.....but trust me.  I have read through multiple threads about the same problem and haven't quite found what I'm looking for, so I'm going to lump all my stuff together here.


My harddrive is dying.  clicking on boot up and shutdown a lot.  Some bad sectors evidentally.

I downloaded ubuntu 7.10 to do a quick dd if=/dev/sda of=/dev/sdb type command.  I received an input/output error when reading the original, damaged, harddrive.

Next, I tried using Acronis Home 11.  Seemed to work fine and everything.  Didn't see any error messages or anything.  Unplugged the first harddrive, tried to boot from the 2nd, nothing.  Keeps bringing me to the system check tools in the bios from Dell.  (yes I know, it's a Dell)


I figure my next bet should be on using dd_rescue or ddrescue.  However I read one post that said it would only copy the information and I would have to do some other, very complicated, things to make it bootable and everything like my original.  Is this true?  If not, is it just like using the "dd" command but using "ddrescue" instead?



So, if anybody could enlighten me I would greatly appreciate it.


Heck, my next move may be popping the Harddrive in the freezer for a while, although since it reads the bad sectors right away when booting I don't think keeping it cold will do much good.


Thanks in advance.

---

### Post by tjbo1m on 2008-04-09
bumpity bump bump......sorry, really didn't want this to drop off the first page.  Hope this isn't a huge rule breaker.

---

### Post by Mausoleum on 2008-04-27
dd_rescue (or ddrescue, two separate programs!) do the same as "dd" (except not stopping on errors and being smart about not skippign too much if there is an error).  So, if you just copy from one whole disk to another whole disk (not partition), you should be fine.

Martin

---

