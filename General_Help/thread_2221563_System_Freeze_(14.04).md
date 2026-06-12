---
title: "System Freeze (14.04)"
date: 2014-05-02
forum: General Help
---

### Post by micheleroviello on 2014-05-02
Hi, I have a problem with the last version of Ubuntu (14.04): the system randomly freezes, so that when it happens I can not use the mouse or the keyboard and the only solution is to power off it.
This also happens with the same version of Xubuntu and Lubuntu. I use the proprietary drivers.
Is there a way to find out what cause this problem?

---

### Post by slooksterpsv on 2014-05-03
If you could get the contents of the dmesg logs that would help.

Post it to pastebin and respond with the link, that would help us to see if it's the proprietary driver. What card is it?

---

### Post by nuttzo31 on 2014-05-03
What sort of graphics card do you have? I found that with my old nvidia 210 graphics i would get regular full freezes and could only reset by holding down the power button, nothing else worked even the reset button.

The freezes stopped when i upgraded to a nvidia 650ti.

---

### Post by micheleroviello on 2014-05-03
Thank you for the answers. I have an Ati Radeon HD 5000 series graphic card.
Here is my[COLOR=#000000] dmesg [/COLOR][http://pastebin.com/iv67Qhjm](http://pastebin.com/iv67Qhjm)
This is the file /var/log/dmesg, but I have found other files in /var/log/ with the name dmesg.0, dmesg.1.gz, dmesg.2.gz and so on.
Should I post one of them in particular?

---

### Post by micheleroviello on 2014-05-03
It is happened again some minutes ago
this is the dmesg: [http://pastebin.com/xvBynMUJ](http://pastebin.com/xvBynMUJ)
and this is the dmesg.0: [http://pastebin.com/x3NBSJnb](http://pastebin.com/x3NBSJnb)
I'd really appreciate your help :(

---

### Post by slooksterpsv on 2014-05-04
From what I can infer on this information, it seems like it may be an issue with the HD5000 graphics in the kernel. If you go to Ubuntu Software Center -> Edit -> Preferences? Sources? something like that -> Additional Drivers - does anything show for your video? If so try installing one of them.

---

### Post by micheleroviello on 2014-05-04
I can install proprietary drivers from there, but I've already done it. However there are two version of them, I'll try to install the other one.
I'll let you know [-o

---

### Post by Diskdoc on 2014-05-09
I'm having this problem too. Found a bug, possibly the same thing: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314871]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314871")

---

### Post by micheleroviello on 2014-05-09
Same problem with the other version of ATI drivers...

---

### Post by wyth on 2014-05-09
Are you running Google Chrome when it freezes? That's a known problem that never seems to get much attention. If so, try this: Open Chrome and go  to chrome://flags. If you've ever messed with the flags in the past, first try resetting them to default. Next, the first two flag options are "Override software rendering list" and "GPU compositing on all pages." Disable both of those (don't leave GPU compositing on Default, set it to Disabled). 

That has seemed to make my system a bit more stable.

---

### Post by micheleroviello on 2014-05-10
Thank you wyth, I'll try your solution

---

### Post by micheleroviello on 2014-05-10
I've tried the solution proposed by wyth, but it doesn't work, the system continue to freeze... ](*,)

**EDIT: **However it happens even when I use Firefox or when I don't use any browser... ](*,)](*,)](*,)

---

