---
title: "System COMPLETELY Destroyed!"
date: 2013-02-20
forum: General Help
---

### Post by rtainc on 2013-02-20
I'd set up a static IP address, and was rebooting the network. I forget what command, but upon doing so, my system crashed and shut down. I tried rebooting, and it would be stuck on "Waiting for network configuration...", "Waiting 60 more seconds...", then "Booting without configuration" (approximately). Anyway, after waiting for about 10 minutes of the messages, I was presented with a "bootup", until reaching a screen, the one in the attachments.

---

### Post by wildmanne39 on 2013-02-20
*Thread moved to **General Help**.*

---

### Post by cortman on 2013-02-20
Try pressing Ctrl+Alt+F1 and see if you can drop into a console. You should be able to restart X from there if indeed that is the problem.
I must say I'm EXTREMELY curious what the last command you entered was.

---

### Post by wildmanne39 on 2013-02-20
>  I must say I'm EXTREMELY curious what the last command you entered was.
Me too.

---

### Post by rtainc on 2013-02-20
I entered a command to restart the network system, I think.

---

### Post by rtainc on 2013-02-20
I'm not a **complete** noob at UNIX systems; I know it's a graphics/GUI issue only. The actual computer can start just fine and connect to the network (in single-user).

---

### Post by tgalati4 on 2013-02-20
Was this a new installation?  What was the hardware?  Did you run memtest for several cycles?  Some computers go wonky with a new linux installation, because the system is stressed in different ways than with a pre-installed operating system.

Simply writing several gigbytes on an old hard drive is enough to cause run-out and then the drive can't read the kernel upon reboot.  Looks like a software problem, but it's really a hardware problem.

If this is a desktop machine, it's time for a cleaning and reseating.

---

### Post by cortman on 2013-02-20
> **rtainc said:**
> I'm not a **complete** noob at UNIX systems; I know it's a graphics/GUI issue only. The actual computer can start just fine and connect to the network (in single-user).

What is the nature of this machine? Are you remotely logging in or using it as a stand alone computer?
Have you tried logging in from the console?

---

