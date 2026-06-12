---
title: "PROBLEM: Can't boot -&gt; Doesn't load MBR"
date: 2007-02-06
forum: General Help
---

### Post by raul_ on 2007-02-06
This thread follows this one:

[http://www.ubuntuforums.org/showthread.php?p=2116231]("http://www.ubuntuforums.org/showthread.php?p=2116231")

It turns error that the error isn't in GRUB anymore, because if i boot from the MBR using SUper Grub Disk i can load fine. No problems at all. So the question is:

Why isn't MBR loaded? I get a blank screen and then some "_" flying and at the end a strange character that looks like a smile and a blinking "_" in front of it (see attachment please). 

Any idea???

[ATTACHMENT]("http://www.ubuntuforums.org/attachment.php?attachmentid=24689&d=1170806926")

---

### Post by r4ik on 2007-02-06
Never seen it before and to be honest it does not look good to me.
If i had that thingy on my screen i would reinstall.
I hope somebody did see it before.

---

### Post by raul_ on 2007-02-06
UPDATE:

Well i tried removing GRUB using the Super Grub Disk, and what it does is pointing MBR do the Windows boot loader (or other OS's) and let it handle it. It worked, because Windows was loaded automatically. Then i tried installing GRUB again from the Live CD:

```

sudo grub
root (hd0,4)
setup (hd0,4)
quit

```

And the problem is back.

It turns out that I can't load from MBR anymore. Maybe that one was a fluke? I get to "Loading stage 1.5" or something like that and then the system freezes and starts beeping.


What I can do is "Boot from GNU/Linux"
I have no idea what to do from here.

---

### Post by raul_ on 2007-02-06
SOLVED!! muahahahaahah

followed these instructions:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_loading_stage1.5]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_loading_stage1.5")

Man this feels good. All I can say is: never reinstall. There is solution for everything

---

### Post by r4ik on 2007-02-07
I bookmarked it congrats on your solution.
Still curious about the thingy though.

---

### Post by jarobata on 2007-10-11
> **raul_ said:**
> SOLVED!! muahahahaahah

followed these instructions:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_loading_stage1.5]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_loading_stage1.5")

Man this feels good. All I can say is: never reinstall. There is solution for everything

What did you do?  That webpage is a wealth of information but I don't know which method you used to solve the problem.

---

