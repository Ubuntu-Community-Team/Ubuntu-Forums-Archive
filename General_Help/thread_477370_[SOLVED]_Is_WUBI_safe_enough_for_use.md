---
title: "[SOLVED] Is WUBI safe enough for use?"
date: 2007-06-18
forum: General Help
---

### Post by mthakur2006 on 2007-06-18
Hi,
I just wanted to know if WUBI is stable enough to use. Also, will it work if I am already dual booting with Fedora Core 6 (which, of course, has its own partition) and using GRUB as the bootloader?
Thanks.

---

### Post by charleseddy on 2007-06-18
WUBI is problematic, but it normally works rather well as long as your hardware is stout enough; if it doesn't you just uninstall it.  And I don't see how dual-booting could affect it.

---

### Post by mthakur2006 on 2007-06-18
does it mess with the MBR?
if so, what is the worse that could possibly happen if things go drastically wrong when installing WUBI?

---

### Post by charleseddy on 2007-06-18
It does not mess with the MBR at all.  It's a Beta test, so the most I could see going wrong is you getting bluescreens.

---

### Post by mthakur2006 on 2007-06-18
so how does it work? and also, will the blue screens come back after restarting? will it delete data? i have the most valuable data in the world on the computer :(

---

### Post by charleseddy on 2007-06-18
It works, literally, by creating a "file" from which Ubuntu is read and booted into.  After an uninstall, no.  The only reason I could see bluescreens is if your HD is going bad and windows gets errors from bad sectors.  No, it does not delete data.

It is perfectly safe, but if it doesn't work you simply boot into windows and uninstall it just like any program.  Try it.  IT WILL NOT HARM ANYTHING.

---

### Post by mthakur2006 on 2007-06-18
sorry to be annoying but have you used it?
if not, am i allright in going ahead with it?
sorry to be so annoying once again.
Thanks.

---

### Post by franck3d on 2007-06-18
I installed ubuntu via wubi on my office computer and have had no issues.
I was also concerned about it's beta status, but so far so good.:p
I have been using it for about a week and booting back and forth between the two OSs several times a day.
Good luck to you if you decide to give it a try.

---

### Post by charleseddy on 2007-06-18
I've also used it on one of my client's computers, and he's had no problems whatsoever.  There's always the possibility of problems, but until you see them you should doubt it's going to happen to you!

ce

---

### Post by mthakur2006 on 2007-06-19
okay cheers for the review.
i will install it when i get home.
btw, do you need an iso file? since the installer is only 10 MB.
thanx.

---

### Post by franck3d on 2007-06-19
when you launch the installer it will download the .iso file for 7.04 alternate
if you already have that iso you can put it in the wubi directory and it will use that.
have fun!

---

### Post by mthakur2006 on 2007-06-19
kk cheers.:KS:KS:KS

---

