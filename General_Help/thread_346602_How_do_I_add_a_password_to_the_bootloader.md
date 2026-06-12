---
title: "How do I add a password to the bootloader?"
date: 2007-01-25
forum: General Help
---

### Post by ardchoille42 on 2007-01-25
I installed Ubuntu 6.06.1 LTS Dapper Drake on a new machine about a week ago. I didn't choose to use a password with the bootloader during install, but now I am seeing that it may help secure the system. 

What are the steps to adding a password to the bootloader **after** Ubuntu is already installed? Do I need to use grub-md5-crypt to hash the password before I add it to /boot/grub/menu.lst? Is that the proper place for the bootloader password? Is there a tutorial on this?

---

### Post by aysiu on 2007-01-25
[HOWTO: Password protect your GRUB entries](http://www.ubuntuforums.org/showthread.php?t=7353)

P.S. If someone has malicious intent and physical access to your machine, you're screwed. This won't help secure your computer.

---

### Post by ardchoille42 on 2007-01-25
> **aysiu said:**
> [HOWTO: Password protect your GRUB entries](http://www.ubuntuforums.org/showthread.php?t=7353)

P.S. If someone has malicious intent and physical access to your machine, you're screwed. This won't help secure your computer.

You're right, good point.

---

### Post by matthewstory on 2007-01-26
while you are screwed if someone has physical access to your computer . . . it's untrue to say that this won't help you secure your machine.  It will in fact make your machine more secure in a lot of different circumstances . . . because in order to beat this you generally have to do something much trickier to get in, and if you want your attack to go undetected, this serves as a substantial gate to jump.  Yes, someone can rip open your box and take your drive, or take the entire box with them, and get to whatever you want (btw, use an encrypted file system if you're that concerned), someone casually plotting destruction will be turned away if they can't just boot into single user mode from the GRUB menu, or execute an arbitrary command in the GRUB terminal without typing a GRUB password first.

So yes, you're still screwed, but your computer is in fact more secure . . . which is why how to do this can be found in every Securing Linux book on the market.

---

### Post by aysiu on 2007-01-26
Thanks for the clarification, matthewstory.

You're absolutely right. It does make your computer a little more secure, but I just didn't want ardchoille to get the impression that security couldn't be compromised with a little bit of effort.

---

