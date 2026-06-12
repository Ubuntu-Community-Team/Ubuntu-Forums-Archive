---
title: "Change GRUB Default"
date: 2006-07-06
forum: General Help
---

### Post by I3rianL on 2006-07-06
How do you change the default OS in GRUB?  Also I have a USB keyboard that wont work with GRUB for some reason.  It works fine with my BIOS just not GRUB.  Does anyone know why?

---

### Post by Jose Catre-Vandis on 2006-07-06
Answer to first question.

when grub loads and shows the boot screen, count the number of lines from the top (including any comment lines) to your preferred default OS
Once you are booted up open a terminal
type
```
sudo gedit /boot/grub/menu.lst
```
enter your password as necessary

gedit will open the menu.lst file which is the config file for grub

Look for Line 14

should say 
```
default 0
```

Remembering the number of lines you counted to, change the 0 to your number

Save, reboot, and see if you counted right, if not repeat as above until correct

---

### Post by I3rianL on 2006-07-07
For some reason when I open up menu.lst with the terminal command nothing shows up the document is just blank.  But when I find menu.lst manually I can see all the text but when I edit it it wont let me save.

---

### Post by jimmygoon on 2006-07-07
> **I3rianL said:**
> For some reason when I open up menu.lst with the terminal command nothing shows up the document is just blank.  But when I find menu.lst manually I can see all the text but when I edit it it wont let me save.

try using a slash at the beginning of the filename 

"sudo gedit /boot/grub/menu.lst"


otherwise you would have to be in the root directory for the above poster's command to work ;)

or you can just do "sudo gedit" and then browse for the file.

grub doesn't support mouses/mice :)

---

### Post by Jose Catre-Vandis on 2006-07-11
> **jimmygoon said:**
> try using a slash at the beginning of the filename 

"sudo gedit /boot/grub/menu.lst"


otherwise you would have to be in the root directory for the above poster's command to work ;)

or you can just do "sudo gedit" and then browse for the file.

grub doesn't support mouses/mice :)

Thx for spotting typo, edit made ](*,)

---

### Post by bsyapril88 on 2008-05-07
Also, the numbering starts 0, 1, 2, etc.
It mentions it in the comments of the file your editing but that step confused me for a bit.

---

