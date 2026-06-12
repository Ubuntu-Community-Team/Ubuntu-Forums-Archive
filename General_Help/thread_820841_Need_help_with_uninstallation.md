---
title: "Need help with uninstallation"
date: 2008-06-06
forum: General Help
---

### Post by wordballoon on 2008-06-06
I just got a new computer and I'm giving this one to my niece, however she doesn't want linux on it because, well she's 9 and doesn't need it. Anway, I run a dualboot with Ubuntu 7.10 and XP, I need to get rid of the Ubuntu partition. Problem is I've lost my Windows XP reinstallation disk. Is there anway I can get rid of ubuntu and GRUB and still be able to use my XP partition. I know i need to fix the MBR but without the reinstallation disk how can I do this? I've heard of [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) but I heard it can run your windows partition. Can anyone help me do this?

---

### Post by wordballoon on 2008-06-06
I really hope this thread doesn't die before anyone answers...

---

### Post by briandu on 2008-06-06
ok so do this 

open xterm

enter: "sudo cfdisk"

select partition 1 and make it bootable

I assume 1 hard disk and it is an IDE so u could refine as 

enter: "sudo cfdisk /dev/hda"

or if new drive then 
enter: "sudo cfdisk /dev/sda"

Check it out and post back

---

### Post by wordballoon on 2008-06-06
alright I'm getting to it now

---

### Post by wordballoon on 2008-06-06
Alright I went in to cfdisk and changed /dev/sda1 to bootable, what should I proceed to do next?

---

