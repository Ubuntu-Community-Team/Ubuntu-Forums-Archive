---
title: "Installing Ubuntu 6.06 onto a Compaq Presario 1240"
date: 2007-12-15
forum: General Help
---

### Post by ToastyMallows on 2007-12-15
Dear Ubuntu Community,

I recently was given the gift of a terrible, old laptop and I figured I'd put a small OS on there, just so I could use it.  I chose Linux, more specifily Ubuntu.  I had Windows 98 before that, and I formated the C drive, and there was no OS what so ever.  I burned Ubuntu 6.06 on a CD-RW, and I've tried over and over to get it to work.

When I start up my Compaq Presario 1240, and it goes past the Compaq splash screen, this is word for word what comes up on the screen:

"CPU = Pentium with MMX 266 MHz
00000640K System RAM Passed
00064512K Extended RAM passed
0512K Cache SRAM passed
Mouse initialized
Fixed Disk 0: HITACHI-DK227A-41
ATAPI CD-Rom: SR2405
ERROR
0270: **Real Time Clock error**

Save to disk partition not found
feature is disabled
Run Phdisk for information file:
create new Partition: CONSULT MANUAL

F1 - Boot
F10 Computer Setup - PhoenixBIOS Setup Utility"

Now I'm not sure whether this has anything to do with my problem, expecially the Real Time Clock error (bold).

The problem I'm having is when I put in Ubuntu 6.06 into the CD-Rom drive, and it uncompresses everything and boots the Kernel, after that I start getting Errors;

```
[209.828974] Buffer I/O error, logical block 178793
[269.823696] Buffer I/O error, logical block 178793
```

I've seen other posts of this nature but I read through most of them and there were no help to me.  Is there anyway that there is another way to install Ubuntu?  Anything I can do about the Real Time Clock error, any suggestions?

Thanks

---

### Post by ToastyMallows on 2007-12-15
Anyone have any suggestions?

---

### Post by philobeddoe on 2008-05-04
Code:
[209.828974] Buffer I/O error, logical block 178793
[269.823696] Buffer I/O error, logical block 178793

Its looks like A Problem with your diskn try a new one and run the check disc option

---

