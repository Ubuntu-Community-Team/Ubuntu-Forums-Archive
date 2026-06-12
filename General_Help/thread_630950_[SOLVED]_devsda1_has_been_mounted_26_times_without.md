---
title: "[SOLVED] /dev/sda1 has been mounted 26 times without being checked, check forced"
date: 2007-12-03
forum: General Help
---

### Post by famous3warriors on 2007-12-03
I have read all the threads that have to do with this but, but I have this problem it hangs at 43.3% and it stays there for a while and never does anything else.  What does that mean?  I had ubuntu 7.10 i386 and did an upgrade to ubuntu studio 7.10 i386.  Do I have to do a complete reinstall.

---

### Post by rosetown on 2007-12-03
I've had the same (only it was 24 times) and it hung in about the same percentage range - but it did complete (about 6 minutes from the message to completion) 

Don't know if this is relevant to you situation.

---

### Post by pointone on 2007-12-04
How long are you waiting for it to complete? If fsck is scanning a large file (DVD image, perhaps?) the progress will not advance until it finishes. Depending on the file size and the speed of your computer, this could take several minutes.

---

### Post by acl123 on 2007-12-04
Don't know what your problem is but I recommend downloading [Autofsk]("https://wiki.ubuntu.com/AutoFsck"). You can change the number of boots before it runs the check (I set mine to 300).

---

### Post by famous3warriors on 2007-12-23
it never finished so I did a complete reinstall of ubuntu 7.10 I really did not have any important information any way.  But now I do I have all my music files and some art class work that I have been working on.  This is the second time that it has done that to me.  I have had the computer on for about 30 minutes now and it is still on about 70.1 %. Is this just a waiting game and leave the puter on till it boots up or do I have to redo everything again?

---

### Post by famous3warriors on 2007-12-23
I found out what actually happened and caused the forced check disk.  I was trying to load music to my wifes Ipod nano and my nephew unplugged the nano.  I shut down the computer and the puter was looking for the nano so as soon as I plugged in the nano the puter started right up.

---

