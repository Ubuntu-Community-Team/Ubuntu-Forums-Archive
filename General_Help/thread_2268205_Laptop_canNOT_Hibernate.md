---
title: "Laptop canNOT Hibernate"
date: 2015-03-06
forum: General Help
---

### Post by New_buntu_89 on 2015-03-06
I recently installed Ubuntu Mate 14.04 on my laptop, and I'd like to be able to set it up to hibernate automatically, or to make it hibernate when I want. However, it seems to be unable to do so. The shutdown window does not provide the option, and neither do the Power Management Preferences menus. Moreover, when u go into the terminal and type

upower -d

it returns (among a bunch of other stuff) this little description:

Daemon:
  daemon-version:  0.9.23
  can-suspend:     yes
  can-hibernate:   no
  on-battery:      yes
  on-low-battery:  no


... which literally says that I cannot hibernate. When installing, I'm pretty sure I didn't make it encrypt the /home folder, and my swap is **twice** as big as my RAM. Is there a way of making this work?

---

### Post by coldraven on 2015-03-07
I don't know the answer to that but I do know that it is probably quicker to boot up than resume from hibernate.
My laptop with a HDD takes about 35 seconds, my friend's similar laptop with a SSD takes 11 seconds. Both running Ubuntu 14.04 and both five year old dual core machines.
As for suspend my laptop takes three seconds, usually the wifi is also working by then.

---

### Post by ajgreeny on 2015-03-07
Hibernation is disabled by default now in all the *ubuntu OSs.

You can enable it again if you want to, but I'm with coldraven in believing that it's a waste of time in most situations, except maybe for a laptop with a really bad battery which will not last long in suspension without losing all power.
See [http://ubuntuforums.org/showthread.php?t=2219403](http://ubuntuforums.org/showthread.php?t=2219403)

---

### Post by New_buntu_89 on 2015-03-11
Thanks, guys. This is the only place I've been informed that hibernation is disabled by default, which is good to know. @ajgreeny, that is exactly my situation. My battery is screwed and I can't afford a new one right now. Also, I tend to leave my computer on and abandon it for a whole day or two, so I like automatic hibernation. For anyone else reading this in the future, I went into that link and followed the instructions of trag. The Terminal returned 4 warnings about being unable to save some things in certain places, but hibernation works fine and it seems to be enabled everywhere. ):P

---

### Post by mattharris4 on 2015-03-12
^ New Buntu, if it helps here Amazon.com sells batteries to many laptops much cheaper than what the manufacturer would sell them for.  For example for my new Toshiba the manufacturer charges $110, Amazon charges $30 for a standard battery and $69 for an extended battery.  My mother's five year old Emachines no longer has parts available from the manufacturer (the battery was about $70 IIRC before they quit selling them), Amazon sells them for between $13 (standard) and $34 (extended).  If the computer is still under warranty an aftermarket battery may be dicey but if the warranty is expired (likely if your battery is failing, if not file a claim with the manufacturer as batteries are usually covered for one year after purchase) there is little harm in using one.

---

### Post by New_buntu_89 on 2015-03-26
Thanks man, I'll consider it, although I'm not in the US anymore. Also, FTR, hibernation isn't being very reliable. Sometimes it fails to recover, and it seems random. I'm using a dual-boot with Windows 7.

---

