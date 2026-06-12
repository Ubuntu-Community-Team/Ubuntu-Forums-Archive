---
title: "Ubuntu installer boots, but then machine immediately restarts"
date: 2005-10-20
forum: General Help
---

### Post by Stuufman on 2005-10-20
As the title of this thread suggests, the I am trying to run the Ubuntu installer. I am currently running Windows XP home. I made myself a Ubuntu 5.10 CD, and I booted with the CD. It took me to the [boot] prompt thing, so I hit enter and it began to work. It ran 2 files that I can't remember the name of, then it booted the kernel. After it does that, the computer restarts and it's as if I had just turned it on. Being in college, I have many friends around with computers, so I tried the CD on a couple different computers. The linux kernel boots fine, and the installer begins. What is the problem? I've been trying this for a couple days now. The same thing happens with Fedore Core 4 install CDs and Debian CDs don't even brng up the [boot] prompt. The computer isn't that old; I got it Dec 2004. This is seriously pissing me off. Any suggestions? I've tried messing with BIOS, but I can't find anything that I can change that may help.

Edit- Sorry, I spelled Ubuntu wrong in the thread title :)

---

### Post by codejunkie on 2005-10-20
[quote=Stuufman]As the title of this thread suggests, the I am trying to run the Ubuntu installer. I am currently running Windows XP home. I made myself a Ubuntu 5.10 CD, and I booted with the CD. It took me to the [boot] prompt thing, so I hit enter and it began to work. It ran 2 files that I can't remember the name of, then it booted the kernel. After it does that, the computer restarts and it's as if I had just turned it on. Being in college, I have many friends around with computers, so I tried the CD on a couple different computers. The linux kernel boots fine, and the installer begins. What is the problem? I've been trying this for a couple days now. The same thing happens with Fedore Core 4 install CDs and Debian CDs don't even brng up the [boot] prompt. The computer isn't that old; I got it Dec 2004. This is seriously pissing me off. Any suggestions? I've tried messing with BIOS, but I can't find anything that I can change that may help.

Edit- Sorry, I spelled Ubuntu wrong in the thread title :)[/quote] 
it's an acpi issue, you have to enter one of these commands at the boot prompt if your using the ubuntu live cd use ```
live acpi=off
``` if your using the install cd use this one ```
linux acpi=off
``` that should solve the rebooting issue let me know if this fixes it.

---

### Post by aysiu on 2005-10-20
[QUOTE=Stuufman]
Edit- Sorry, I spelled Ubuntu wrong in the thread title :)[/QUOTE] I fixed the spelling.

By the way, I don't know what the solution is, but it seems you've done a pretty good job of diagnosing the problem yourself--something's wrong with your computer if every disk messes up on your computer and works on your friends' computers.

Anyone have ideas what this could be?

**Edit**: Oops. I guess codejunkie knows what the problem is.

---

### Post by Stuufman on 2005-10-20
Thank you. I appreciate it. I'll try it and get back to you.

---

### Post by RAOF on 2005-10-20
The problem could be in the acpi or apci or some other four-letter-acronym support of your motherboard.

Try booting the from the boot prompt try adding the noapci and acpi=off options.  I think that would be with "linux noapci acpi=off" at the boot prompt, but I'm not sure.

Edit:  Whoops.  Too slow :)

---

### Post by Stuufman on 2005-10-20
Yep, the acpi=off thing worked. Thank you very much, I appreciate it.

---

### Post by codejunkie on 2005-10-20
[quote=Stuufman]Yep, the acpi=off thing worked. Thank you very much, I appreciate it.[/quote] glad you got it working and welcome to the forum.

---

