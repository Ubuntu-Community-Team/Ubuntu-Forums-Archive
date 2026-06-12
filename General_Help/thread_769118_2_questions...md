---
title: "2 questions.."
date: 2008-04-26
forum: General Help
---

### Post by chrisx16x2008 on 2008-04-26
how can i turn graphical boot on using only the terminal? and using recovery mode/root user is it possible to recovery your system(i.e. make it like it was a few days ago, before a problem occured?)

---

### Post by p_quarles on 2008-04-26
I'm not sure what you mean by "graphical boot using only the terminal". Do you want to enable the bootsplash screen for recovery mode? Or make the change via a terminal-based application? Or what?

And, yes, recovery mode allows you to rescue the system in some cases, but unless you have a backup, there is no "restore system the way it was a few days ago" command.

---

### Post by ibuclaw on 2008-04-26
A) You'd have to back up the boot file.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Then inside the file, on the "kernel" line of the boot you want to change, add splash as one of the arguments.

ie:
From
```
kernel /boot/blah-linux root=UUID=blah-harddrive ro quiet rootflags=data=writeback
```
To
```
kernel /boot/blah-linux root=UUID=blah-harddrive ro quiet **splash** rootflags=data=writeback
```

But **do not** under any circumstances copy those lines exactly! They are specific to my computer and my computer only!


B) Yes, what q_charles said.
You can! but you'll have to set up something such as a cronjob to backup your PC on an daily or period basis.

Regards
Iain

---

### Post by chrisx16x2008 on 2008-04-26
what you mean a back up? the reason i was wondering bout this is because i turned the graphical boot off then restarted my system and it does show the splash load screen but then goes to something tht says.. no resume image, booting normally...

Kernel Alive

but nothing else happened after tht

---

### Post by ghost_ryder35 on 2008-04-26
how long did it sit doing nothing after it said "kernel alive"

---

### Post by chrisx16x2008 on 2008-04-26
it sat atleast 30 minutes

---

