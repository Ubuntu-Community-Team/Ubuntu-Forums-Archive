---
title: "Grub: Boot straight to windows on exit?"
date: 2006-11-16
forum: General Help
---

### Post by jrings on 2006-11-16
At work, I use a dual-boot system with SuSE, and there it is possible to get an option on the exit switch so that it will reboot straight to Windows on exiting from Linux.
I haven't found how to do this in (K)ubuntu, or whether it is possible. This would be very helpful, because you don't have to sit there and wait for the boot menu to show up. Or to forget to wait and boot Linux once again.
Is is possible to get this option from grub? A shell command would be ok as well if nothing else works.

---

### Post by Tomosaur on 2006-11-16
It is possible yes, but I can't remember the specifics of it at this particular moment. It involves using the 'savedefault' line in /boot/grub/menu.lst I think.

---

### Post by Jongi on 2006-11-16
I think you need to get the "proper" kde for that. Not the one tailored for kubuntu. I base this on the fact that I never got the same feature in Fedora when updating from the fedora repositories, but got it when I updated from the actual kde repo.

---

### Post by jrings on 2006-11-16
Hmm but maybe it is a feature tailored for these distributions, like a script or something. I just don't have a real idea what search terms to use to look for this feature :(

---

### Post by Jongi on 2006-11-16
Nope it seems I am talking crap

---

### Post by vruum on 2006-11-16
there's a script called grub-reboot (/sbin/grub-reboot) that does this, it's part of the grub package so it should already be installed. It looks pretty simple ```
 sudo grub-reboot 1
``` reboots into the second option in the grub menu (the first option being 0) I don't know about a graphical one though.

---

### Post by jrings on 2006-11-17
Well I tried this.
The script was installed, it saved something with save-default and rebooted, but grub came up like normal, didn't work :(

---

### Post by Osanya on 2006-11-17
edit /boot/grub/menu.lst 
make the windows entry the default option

Grub will load, windows will be highlighted, when the timer goes out, it will boot windows.

you'll have to be patient for the whole 10 seconds... or you could reduce the timer to a few seconds if you want.

---

### Post by jrings on 2006-11-17
No, I definitely don't want to make Windows default. I boot Linux by default and want to go to Windows only occasionally.

---

### Post by wowtip on 2006-12-15
I am also thinking about this, and tried a couple of solutions. No luck so far though... Anyone have anything to add?

Also, it would be nice if it worked both from Ubuntu and Windows. But I guess you would have to use another boot manager for that to work, if even possible.

---

### Post by hikaricore on 2006-12-15
You could always keep a windows boot floppy in the drive.
And pop that in when you reboot thus bypassing Grub.

When you're done just pop it out again for easy one push access.  =)

---

