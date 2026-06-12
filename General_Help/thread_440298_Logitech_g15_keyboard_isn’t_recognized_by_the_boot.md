---
title: "Logitech g15 keyboard isn’t recognized by the boot loader."
date: 2007-05-11
forum: General Help
---

### Post by Caseyphillips on 2007-05-11
Looks like Wubi install went ok but when the boot loader app pops up I am unable to scroll down and select Ubuntu to boot instead of XP. Anyone have any ideas how one could fix this? I am using a Logitech G15 keyboard by the way.
-Casey

---

### Post by ago on 2007-05-11
Casey that is a windows issue (ntldr), you would probably have the same problem if dualbooting between Xp and 98...

---

### Post by Caseyphillips on 2007-05-11
Humm well other then getting a new keyboard is there anyway around this. I would really like to try out Ubuntu :)

---

### Post by ago on 2007-05-11
Don't know about the windows side, but you can test whether grldr is better than ntldr at detecting the keyboard. Set it as default boot option, then in C:\menu.lst, comment out hidemenu and set the timeout to 10 so that the grub menu shows up. When the menu appears see if you can use the keyboard, if so you may want to use grub.mbr (see the grub4dos wiki for instructions).

Better have a second keyboard handy...

---

### Post by Caseyphillips on 2007-05-11
He he or really like Ubuntu... going to give it a shot.. brb... I hope..

---

### Post by Caseyphillips on 2007-05-11
Prehaps I misunderstood the directions but I basically up Ubuntu to be the 1 choice for statrting up and did the modifications to the file that you suggested. The windows bootloader still showed up after its count down though it went to Grub(think that is the name) in which Ubuntu was the only listing (and it seemed like the keyboard was unresponsive there was well). Shrug.

---

### Post by ago on 2007-05-11
Even if you have 1 item you can see if you can press "c" or "esc"...

If you want to add another item to test the arrow keys, append the following at the end of the file:

title command line
commandline

---

### Post by Caseyphillips on 2007-05-11
GIving it a shot... side note Ubuntu is hella nice.... I guess understand what all the fuss has been about ;)

---

### Post by KnightZero77 on 2007-05-11
I had a similar problem after installing Ubuntu on my PC as well.  In my case, the USB keyboard was not being recognized from the BIOS level.  In my PC's Phoenix BIOS, there was an option to set USB keyboards to be managed by the BIOS instead of the OS.  My motherboard had it set, by default, to be managed by the OS.  You might want to see if your BIOS has a similar option.

:Edit:  I, in fact, am also using a Logitech G15 keyboard.  Just thought I'd clarify.

---

### Post by Caseyphillips on 2007-05-11
Thanks Knight I will check that right now :)

---

### Post by Caseyphillips on 2007-05-11
Knight you are my hero. That did it although it was called something else in my BIOS. Thanks so much for the help guys.

---

### Post by whinub on 2007-05-13
strange...i have a G15 and had no trouble selecting Ubuntu

---

### Post by Caseyphillips on 2007-05-13
> **whinub said:**
> strange...i have a G15 and had no trouble selecting Ubuntu

I probably because your BIOS was already configured to handle USB keyboards before the OS. Mine was configued to not handle them and let the OS handle them. When the loader actually loaded it does so with out USB keyboard support.

---

