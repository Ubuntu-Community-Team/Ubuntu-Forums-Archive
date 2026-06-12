---
title: "Microsoft office 2003 wont work with crossover please help!"
date: 2008-05-14
forum: General Help
---

### Post by Chris_aus on 2008-05-14
Hey guys I just installed linux two days ago and i absolutely know nothing. I downloaded and installed crossover office 6.2.0 (at least i think i did) and when i go to install office it says "newer window version needed" does anyone know whats going on? btw i have ubuntu 8.2 dual booted with xp

the other thing where does the trial version of crossover office get saved to. there are literally no files on my computer refering to crossover office? however it is installed!

cheers chris

---

### Post by pointone on 2008-05-14
I've never used CrossOver, but it's based off the same codebase as Wine, and Wine has an option to change the version of Windows that is "emulated" (but not emulated... :P) By default, Wine usually sets Windows 98. See if you can find a similar option and change it to Windows XP.

---

### Post by Mr.Johnny on 2008-05-14
open a terminal and type winecfg ;)

---

### Post by Claus7 on 2008-05-15
Hello,

as far as the files are concerned you should look in .cxoffice (mind the dot). In order to see that, open a terminal and type cd .cxoffice and then navigate to the files you want. 

As far as the message you get, I have to tell you that sometimes I had to install crossover even a third time in order for it to work nicely. I would propose you to remove it entirely and then install it again.

Regards!

---

