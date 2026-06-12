---
title: "dumb USB question"
date: 2007-11-18
forum: General Help
---

### Post by spipe on 2007-11-18
I like to use a fast low-resources window manager (icewm) for various reasons, but one situation where I get tripped up is when connecting a USB storage device such as an SD card reader.  In the standard desktop environment the mount is automatic; it's not really what I want, but I can at least get to the data that way.  I've been switching back and forth between desktops now and then just for this one issue.

There must be some well-defined way of using the information returned from "lsusb" (or something else?) and setting up a corresponding /dev file and fstab entry so I can mount USB filesystems from the command line.

Understand I'm not really looking for a way to run an automounter process under icewm, but am more interested in lower-level stuff I can work into scripts.  Somebody give me a little nudge please, even if it's an RTFM with some clue as to where I should start reading.

Thanks.

---

### Post by spipe on 2007-11-18
Well this is how it often goes.... I do a few searches on a particular issue, don't find an answer, post a question, and the act of posting the question gives me an idea for a better search.  Ain't forums wonderful!

In case someone else finds this thread in a similar search, let me just say these two things:

[FONT="Lucida Console"]blkid[/FONT]

  ...or...

[FONT="Lucida Console"]  fdisk -l[/FONT]


Godspeed all. :)

---

### Post by Chilli Bob on 2007-11-30
OK, so I can see my USB memory stick, but I still can't access it.

---

