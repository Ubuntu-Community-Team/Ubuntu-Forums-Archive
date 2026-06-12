---
title: "Error 17?"
date: 2007-07-09
forum: General Help
---

### Post by jalmcbj on 2007-07-09
My computer (running Ubuntu v6.06, last I checked) crashed when I attached my MP3 player to upload some music (I have an RCA Lyra, if that matters). Now, whenever I go to start it up, it says the usual "GRUB loading", but after a few seconds of loading says "Error 17".

What does this mean, and how can I fix it?

---

### Post by Trebaruna on 2007-07-09
[_This site_]("http://www.uruk.org/orig-grub/errors.html#stage2") reports error 17 means this:

> 17 : "Invalid device requested"

This error is returned if a device string is recognizable but does not fall under the other device errors.
I am afraid, however, that I've no idea what it means.
I'd say your best bet is to reinstall GRUB.

Hang on while I try and get a link to a nice guide...

EDIT: [Here you go]("http://www.sorgonet.com/linux/grubrestore/")

---

### Post by poohbear1616 on 2007-07-09
Here is another link with all kinds of grub info:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#17")

I linked it right to your error code.

---

### Post by jalmcbj on 2007-07-09
Trebaruna, thanks for the effort, but I don't believe that guide is too helpful with my problem. I have Ubuntu solely on my computer, no Windows, and I believe that guide's suggestions has to do with problems when the drive is partitioned for both OS's.

The link that you gave, poohbear, is slightly confusing to me. I don't know what the Super GRUB disk is, but would my Ubuntu install disk work? I tried the solution he links to at the bottom of the description of Error 17, but I think it may have made my BIOS unable to recognize my CD drive, which could cause huge problems considering my floppy drive hasn't worked for 2 years, so I don't have many options left, I think.

EDIT: Never mind about the CD drive. It's working again. I just had to put a disk in there.

EDIT 2: I think the problem may have actually been with my hard drive. I tried re-installing Ubuntu, but it couldn't even format my hard drive. I'm ordering a new one, and I'm gonna put that in once I get it. That'll solve the problem for good, even though I'll lose all my files. Oh well, I didn't have anything too important on there anyways.

---

