---
title: "Ubuntu freezes - Windows runs fine. Please help."
date: 2007-09-07
forum: General Help
---

### Post by efjen on 2007-09-07
Hello all.

I have been running Ubuntu 7.04 for several months on my computer, and I never encountered a problem with it until now. About a week ago, the screen froze on my Gnome desktop. No mouse or keyboard input helped. (I tried Ctrl+Alt+Bksp.) I had to power down my computer manually.

After this crash, Ubuntu locks up the same way every time I use it. Sometimes it freezes at the GDM login, but more frequently, it freezes after 5-15 minutes of use. I have not made any changes to the computer's hardware.

I have tried to reinstall Ubuntu from scratch, but the live CD freezes in the manner. I have not made any hardware changes to my computer, and as I stated, I have run Ubuntu on it for several months without a problem. Windows Vista runs perfect on the same computer. (dual boot)

I really want to get Ubuntu running again, but I'm confused as to why it crashes. I'm thinking there is something wrong with my hardware, since the live CD also crashes. However, as Vista runs with no problems, I'm confused.

I'm a Linux newbie, and would very much appreciate help to solving my problem. I don't want to be stuck using Vista!

Thank you.

- Erlend

---

### Post by bogdan_5844 on 2007-09-07
well...try this:
if you can,check the cd with the Check CD for Errors option,it may be just a broken disc
if not,try borrowing a CD unit from a friend,see if that works,or try downloading the Ubuntu disc again...can't really think about anything else:confused:

---

### Post by efjen on 2007-09-07
> **bogdan_5844 said:**
> well...try this:
if you can,check the cd with the Check CD for Errors option,it may be just a broken disc
if not,try borrowing a CD unit from a friend,see if that works,or try downloading the Ubuntu disc again...can't really think about anything else:confused:

Thanks.

I have checked the CD, and it reported no errors. It is the same disc that I installed Ubuntu from originally, and back then it all worked. No hardware has been changed since then. It's strange that it all works under Windows, if I in fact do have defect hardware.

---

### Post by Inquisitive Alex on 2007-09-07
Maybe this is a hardware issue... I had the similar problem. I checked memory (with memtest86). There were errors. I have to change one memory module and everything works fine now.

---

### Post by Kobalt on 2007-09-07
Can you please post some more details about your hardware configuration : cpu, motherboard, HD, etc...

---

### Post by tech9 on 2007-09-07
> **efjen said:**
> Hello all.

I have been running Ubuntu 7.04 for several months on my computer, and I never encountered a problem with it until now. About a week ago, the screen froze on my Gnome desktop. No mouse or keyboard input helped. (I tried Ctrl+Alt+Bksp.) I had to power down my computer manually.

After this crash, Ubuntu locks up the same way every time I use it. Sometimes it freezes at the GDM login, but more frequently, it freezes after 5-15 minutes of use. I have not made any changes to the computer's hardware.

I have tried to reinstall Ubuntu from scratch, but the live CD freezes in the manner. I have not made any hardware changes to my computer, and as I stated, I have run Ubuntu on it for several months without a problem. Windows Vista runs perfect on the same computer. (dual boot)

I really want to get Ubuntu running again, but I'm confused as to why it crashes. I'm thinking there is something wrong with my hardware, since the live CD also crashes. However, as Vista runs with no problems, I'm confused.

I'm a Linux newbie, and would very much appreciate help to solving my problem. I don't want to be stuck using Vista!

Thank you.

- Erlend

Sounds like a hardware issue... please list your hardware specs

---

### Post by jnorthr on 2007-09-07
if you can get a terminal session up, try the  command:
dmesg
this shows the log of most recent kernel activity, from that we may be able to diagnose your system problems more easily. If you can post the tail of that output it may give us further clues.
Thx

---

