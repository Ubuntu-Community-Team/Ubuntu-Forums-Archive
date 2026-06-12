---
title: "No windows option in grub??"
date: 2007-04-23
forum: General Help
---

### Post by chromesky on 2007-04-23
i installed ubuntu, then windows, which wrote over grub. then i booted the live cd and ran some commands that i was told would get ubuntu to run. now ONLY ubuntu runs with no option to enter windows. how could i get grub to work normally, aside from reinstalling ubuntu. how could i boot windows?

---

### Post by chromesky on 2007-04-23
also, i do hit escape to get the list, and windows isn't listed.

help wld be much appreciated

---

### Post by chromesky on 2007-04-23
also, how do i run the ubuntu text editor as root? maybe i could hack some commands to /boot/grub/menu.lst??

---

### Post by Tsen on 2007-04-23
You'll need to edit menu.lst, yes.
From the terminal,
```
sudo gedit /boot/grub/menu.lst
```
Edit it to add a Windows entry (google it if you need, there's several tutorials how).
Bing! You're done.

---

### Post by chromesky on 2007-04-23
adding
"title Windows XP
root (hd0,0) #hd0,0 because the windows disk was called sda1 by linux
makeactive
chainloader +1"
and escaping to the selector screen at boot (in grub) yields the following error message:
"Error 13: Invalid or unsupported executable format"

I'm fooled by all this . . .

is there an easy resolution?

---

### Post by chromesky on 2007-04-23
that error 13 is after i select Windows XP from the escape list

---

