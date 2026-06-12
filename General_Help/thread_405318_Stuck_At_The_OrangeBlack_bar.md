---
title: "Stuck At The OrangeBlack bar"
date: 2007-04-09
forum: General Help
---

### Post by Bobberb on 2007-04-09
So, I installed ubuntu using the alternate cd because the desktop live cd cannot get into the LIVE OS.

Anyhoo - I turn on my computer, bios loads, then grub, then the ubuntu orange on black 20 block load bar comes up. It loads a little and then stops at 15% (or 3/20 blocks).  I waited 1 hour  and I even reinstalled 	](*,)	](*,)	](*,)	](*,)	](*,)

HELP!!

specs: Dell Dimension 4500S

---

### Post by Bobberb on 2007-04-09
bump

---

### Post by Bobberb on 2007-04-09
bump

---

### Post by mcduck on 2007-04-10
You could try pressing Ctrl-Alt-F1 during the boot to see the text messages instead of graphical boot. Then you should at least be able to find out where the boot freezes.

---

### Post by Bobberb on 2007-04-10
no, It kills my keyboard as soon as the splash comes up

---

### Post by mcduck on 2007-04-10
> **Bobberb said:**
> no, It kills my keyboard as soon as the splash comes up

Then try booting into recovery mode, as it doesn't use splash by default. If that works, remove 'splash' from the normal boot line in /boot/grub/menu.lst to get rid of the splash screen until you get the problem fixed.

---

### Post by Bobberb on 2007-04-10
> **mcduck said:**
> Then try booting into recovery mode, as it doesn't use splash by default. If that works, remove 'splash' from the normal boot line in /boot/grub/menu.lst to get rid of the splash screen until you get the problem fixed.
By splash I mean this thing (not version of Ubuntu I am using and no text in mine)
[http://www.zdnet.com.au/shared/images/news/ubuntu/bootscreen.gif](http://www.zdnet.com.au/shared/images/news/ubuntu/bootscreen.gif)

I'll try that

---

### Post by Bobberb on 2007-04-10
Ok, Well, recovery does not work, it gets stuck on loading something like [   39.#####].  I just took out splash from the line and it is now loading a giant list of [###.######].  Please tell me I will not have to do this everytime...does Ubuntu have hibernate like windows???


If this works - thank you

---

### Post by pointone on 2007-04-10
The [#####] is the timestamp, which doesn't really help us much. Please post the information *after* the number; the last two or three lines displayed before the systetm locks up.

---

### Post by Bobberb on 2007-04-10
No lock up when I took splash out - recovery failed but it said "fixing(ed) recursive problem, but needs to reboot.  It happens every time.   I am going to go check on the computer.

---

### Post by Bobberb on 2007-04-10
Ok, it is still running - If I remember correctly it said "loading hardware drivers"

---

### Post by Bobberb on 2007-04-10
it has been going on for 25 minutes (I took out splash from the CL)

loading...loading...loading

---

