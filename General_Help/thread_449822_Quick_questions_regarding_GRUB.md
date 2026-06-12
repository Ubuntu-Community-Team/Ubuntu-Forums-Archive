---
title: "Quick questions regarding GRUB"
date: 2007-05-20
forum: General Help
---

### Post by disconnecting on 2007-05-20
I love ubuntu, but I was wondering if I could alter the GRUB settings to make windows the default selection so I don't have to pay attention during the boot sequence.

Also, every time I restart after installing ubuntu my date/time settings in Windows revert back an hour, and I was wondering if anybody else came across this problem and knew how to fix it. I've been late to work a few times now forgetting about this little issue (using my computer as my alarm clock), and would like to worry about it no longer. Any help is greatly appreciated, thanks!

---

### Post by kdarkentity on 2007-05-20
i dont know of anyway to change the grub boot order however im sure it can be done...also i have run in to the same problem with the clock in windows only mine is two hours behind each time

---

### Post by nerdman978 on 2007-05-20
It's actually really easy. 

> sudo gedit /boot/grub/menu.lst

Then you need to look for the default entry which should read 0. Then count the number of title lines from the start of the file to the title line for (you use Windows right?) Windows, starting with 0 (don't count lines beginning with #). For example, if your Windows install is on the fourth title line (it is if all you have installed is ubuntu and windows) set the default to three. Now Windows is your default (or first) choice in the bootloader.

---

### Post by bobplano on 2007-05-20
you need to change the grub file 
```
gksudo gedit /boot/grub/menu.lst
```
then you change the default at around line 14. i'm not really sure what to do next so just back the file up for now

---

### Post by m.musashi on 2007-05-20
Just an FYI. Changing the default will work fine until you get a kernel update. Then you will have a couple new lines added and if windows was 4 it's now 6. It's not a big deal and is easily fixed by editing menu.lst but something to be aware of.

---

