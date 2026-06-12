---
title: "can't burn iso image"
date: 2006-12-28
forum: General Help
---

### Post by pagingmrherman on 2006-12-28
Hi, I've got ubuntu 6.10 installed and for some reason, I can't burn an iso image to my cd burner.  I right click on the iso file, click on 'write to disk' and everything looks like it's going to work but every time I click on 'write' it just keeps asking to put a blank disc in the drive.  Even though there already is one in the drive, it just keeps asking for one.

Also, when I put a blank disk in the drive, I get a 'cd-rom disc' icon on the desktop.  when I go to the burn:/// location in nautilus, I try to click 'write to disc' and it asks me if I want to create the image from the ISO file, I tell it to and it doesn't do anything at all.

what's the command line for burning ISO's???

Thanks in advance,

PW

---

### Post by s6dalane on 2006-12-28
Maybe you should try burning that .iso with **Brasero** or **Gnomebaker**. I believe that you can install both via Synaptic.

---

### Post by cactaur on 2006-12-28
You can also right-click the .iso image and select Write to CD. That might work. I've always had trouble with the CD/DVD burner.

---

### Post by wpshooter on 2006-12-28
First, You are sure that your CD drive is write capable ?

Then the real answer is to go to ADD/REMOVE programs and search for and install the **K3b** CD burner program.  Wala, problem solved !!!

---

### Post by pagingmrherman on 2006-12-28
Well, gnomebaker seemed to work but god knows why the other built-in 'write to disc' didn't.  It did give me some error about suid blah blah but it worked anyways.  Oh well, maybe they'll get it to work right one of these days....

---

