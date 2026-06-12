---
title: "Problem applying patch then make oldconfig &amp; xconfig problems"
date: 2007-03-10
forum: General Help
---

### Post by crispBH on 2007-03-10
Hi

I've been following the howto on compiling a new kernel here: [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)

All went well until I came to apply the patch.  I issued the command

```

root@spag:/usr/src# bzcat patch-2.6.20.2.bz2 | patch -p1

```

and I get prompts like this (this was actually the last one) 

```

can't find file to patch at input line 4730
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git a/sound/usb/usbaudio.c b/sound/usb/usbaudio.c
|index 19bdcc7..1bd9af6 100644
|--- a/sound/usb/usbaudio.c
|+++ b/sound/usb/usbaudio.c
--------------------------
File to patch: Skip this patch? [y]
Skipping patch.
6 out of 6 hunks ignored

```

I can (and) did skip all of these, but obviously that doesn't seem to be what should be going on.  I skipped through 50 or so at a guess (well, a lot) and then it brings me back to the command prompt after that last one.

I wasn't convinced this was right, and my next problem may or may not be linked.  When I type make oldconfig and make xconfig, I get the following error:

```

root@spag:/usr/src# sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make xconfig
make: *** No rule to make target `oldconfig'. Stop.

```

I definitly have the latest version of build-essential installed too.  Any thoughts on what this could be?

Thanks in advance!

---

### Post by emparq on 2007-05-03
```
root@spag:/usr/src#
```

looks like your in the /usr/src dir when you should be in the /usr/src/linux dir?

---

