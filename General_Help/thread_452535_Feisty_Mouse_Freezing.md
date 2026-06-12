---
title: "Feisty: Mouse Freezing"
date: 2007-05-23
forum: General Help
---

### Post by rgx on 2007-05-23
My mouse has been randomly freezing on just about a fresh install of Feisty. The mouse freezes but the keyboard and feisty are still functional. I can alt+tab and FF..etc are still working. 

I did install nvidia drivers that included changes to the xorg.conf file but my mouse had froze prior to that install.

Are there any settings/configurations that may be the cause this? I want to avoid rebooting just to get my mouse working again.

Edit:
My system specs

Dell Dimension E521
Feisty x86
AMD Athlon 3800+  64 x2
Nvidia GeForce 7300 LE pci-e
plain old dell optical mouse

---

### Post by eejk on 2007-05-23
same problem here i'ts driving me nuts. it only seems to happen for me when i am running vmware workstation

psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
psmouse.c: TouchPad at isa0060/serio1/input0 lost sync at byte 1
psmouse.c: issuing reconnect request

then the mouse just stops working.

hp dv9000
Intel EMT64
2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

---

### Post by grogger13 on 2007-05-23
i have an even worse problem with Feisty, i will either boot or re-log in and then the caps lock and num lock light will be blnking and the computer wont respond.  Alt+ctrl+backscape also doesn't do anything,  im not sure if Raising skinny elephants is utterly boring or whatever that is works, becuase im not sure how to do it.

Everyone says that linux doesn't have to reboot, but i have to in this spot.

---

### Post by rgx on 2007-05-23
I may try going back to Edgy which I have running at home. The issue with this Fiesty problem is that it is my work computer. A co-worker installed the same copy and hasn't had a problem. Luckily I left my Windows XP partition intact so I could be productive at work today. Though I was looking forward to being productive in Ubuntu.

---

### Post by eejk on 2007-05-24
bump... nobody has any suggestions?

---

### Post by agentx on 2007-05-24
I have the same problems and even though I've tried just about everything (from using the evdev driver for my mouse to booting with acpi=off or acpi=force icqpol) it didn't solve anything. The mouse just kept on freezing randomly after logging in.  
It's an USB mouse that worked with no problems on Edgy. Even tried different manufacturers, the same thing. Now after a quick search on ubuntu's bug report's on launchpad i've noticed that this isn't a Ubuntu bug only, it's a bug in the new linux kernel 2.6.20, so it may happen on any other distribution that uses it.
Tried this too and yes, on every single distribution that used linux kernel 2.6.20 and up the mouse was freezing randomly after logging in.

The bug report is [here]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108382") and the temporary solution is this [script]("http://librarian.launchpad.net/7583925/unsupported-patch-for-87262.sh").
It worked for me, but I still have some issues with installing some packages now.

---

### Post by rgx on 2007-05-24
Bug linked there has to do with ps/2 mice. I've had the problem with my usb mouse. I'm on a fresh install of Feisty to see if it occurs again. My edgy disc is standing by.

---

### Post by eejk on 2007-05-25
thanks agentx i'm gonna try the patch

---

