---
title: "fglrxinfo ERROR: DDX driver fingerprint mismatch"
date: 2007-01-14
forum: General Help
---

### Post by Brightrock on 2007-01-14
Hi,

I recently made the mistake of trying to make aiglx work on Dell 9300 with an ATI x300.  Before I started working on this beryl and my graphics driver worked fine.  Now fglrxinfo always tells me I'm using the mesa gl stuff and the driver doesn't seem to work--or at least not well.  Here's the fglrxinfo output:

ERROR: DDX driver fingerprint mismatch: got 0x7A3E2CF0, but expected 0x32C4A39B
libGL error: InitDriver failed
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I can't find anything out about the DDX mismatch on these forums although when I google the issue I get this.

[http://www.linuxquestions.org/questions/showthread.php?t=492770&referrerid=195877](http://www.linuxquestions.org/questions/showthread.php?t=492770&referrerid=195877)

which makes it look like the new kernel will solve the problem.  However, do I have to wait until Ubuntu updates?  Is there some solution before that.  Anyone else out there dealt with this problem?

Also I'm running edgy and have recently (in the process of trying to get this to work) updated my xorg.conf (installed breezy originally).  (Don't worry I've followed the guides and modified the xorg.conf as needed for the fglrx driver. Still doesn't work.)

Thanks,

BR

---

### Post by sevenearths on 2008-03-19
I've got a similar problem

```
arthur@laptop:~$ fglrxinfo
ERROR: DDX driver fingerprint mismatch: got 0x9BA30552, but expected 0x517DC51A
libGL error: InitDriver failed
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 1.4 (2.1.7412 Release)

```

---

### Post by danwood76 on 2008-03-19
This thread is very old and the OP was trying to get Aiglx working on a driver that didnt support it.
If you have a problem your better off starting a new thread.

To me it sounds like you have either not got fglrx installed correctly of your xorg.conf is messed up.
Try re installing fglrx and running the 'aticonfig --initial' command

---

### Post by sevenearths on 2008-03-19
> **danwood76 said:**
> This thread is very old and the OP was trying to get Aiglx working on a driver that didnt support it.
If you have a problem your better off starting a new thread.

To me it sounds like you have either not got fglrx installed correctly of your xorg.conf is messed up.
Try re installing fglrx and running the 'aticonfig --initial' command

```
arthur@laptop:~$ aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

```

I do have another thread ([here]("http://ubuntuforums.org/showthread.php?t=728304")) butno one has posted on it so I thought I would post here.

Have you got any other ideas of what it might be?

I've tried installing the driver through the restricted driver window and envy, but to little success :(

---

