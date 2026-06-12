---
title: "nouveau failed"
date: 2014-12-05
forum: General Help
---

### Post by haberberger53 on 2014-12-05
My computer's been locking up once in a while, for a while, and then recently the graphics failed and I have only a checkerboard like pattern for graphics.  Was able to boot to recovery mode, and in root shell execute a "mount -o remount,rw /" command, which fixed the problem until it crashed again shortly thereafter. Was also able to view an error report that said "nouveau failed" among other things.
I don't have a clue what I'm doing.
I'm running 14.04 on a 7 year old Dell Inspiron, 64 bit, 1Gb memory.
Had to fuss with the graphics driver when I loaded 14.04 but it's worked until now.
I suspect a hardware problem just because of it's age. It seems to run slower, and I hear the hard drive grinding away alot.
Is it time to buy a new computer?
Are there any tests I can run to see what the problem is?
I saw that there is an ubuntu light operating system that might be better for older systems. Is that an option?
thanks for any help
Jim

---

### Post by nerdtron on 2014-12-05
chkerboard pattern   -----> video problems (in hardware). same experience when the on board video of my motherboard died.
nouveau failed ----> if hardware has problems, so will the software running on it.
hard drive grinding away alot -------> old hard drives are a bit noisy when you read/write on them. but if it is grinding (maybe spinning too much) or clicking, it's time to find a replacement.

---

### Post by mörgæs on 2014-12-05
> **haberberger53 said:**
> 
I saw that there is an ubuntu light operating system that might be better for older systems. Is that an option?


Yes, definitely. You shouldn't consider buying more stuff before you have tried a fresh install of Lubuntu.
More info in the link in my signature.

---

