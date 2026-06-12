---
title: "how to start right on the terminal"
date: 2007-05-31
forum: General Help
---

### Post by ahura on 2007-05-31
I instaled Ubuntu, configured to go straight to the graphic login screen! But now i cant start any kind of session coz i got 0mb of space while compiling.. so, i need a button, a trick, anything, to start ubuntu right into the terminal, so there would be no need (or no?) to start a session, so i could erase stuff.. what about? please help, i need badly to feel linux again *_________*

---

### Post by 67GTA on 2007-05-31
You can boot into recovery mode at the grub screen and be at a text prompt. Terminal heaven :D

---

### Post by ago on 2007-05-31
ctr + alt + f3
or press esc after you select ubuntu
or edit c:\wubi\boot\grub\menu.lst, remove hidemenu and increase timeout, then select recovery mode

---

### Post by ahura on 2007-05-31
thanks! but i am definitely too noob to do that, i dont have any idea on how to remove that strings and how to set others on that text, i'll end up screwing everything... but thanks anyway... Ubuntu: 1 x Me: 0

---

### Post by minhmeoke on 2007-05-31
Here is a step-by-step description of how to boot into recovery mode:

1) Restart your computer, then select "Ubuntu" at the GRUB bootloader menu (the other choice should be windows).

2) Right after you select Ubuntu and hit enter, press the "esc" key rapidly. If you were fast enough, another menu should appear almost instantly. There should be 3 choices, the first one is default mode, the second is the recovery mode, and the third is a memory test.

3) Choose the second choice, it should be something like "Ubuntu kernel 2.6.20-15 generic (recovery mode)".

You have to press the "esc" key really fast, or else it will keep on booting the default version instead of showing you the menu. It might take a few tries... Good Luck!

---

### Post by ahura on 2007-06-01
thx vry much 67GTA, ago and minhmeoke! I did it, cleaned some space and here i am riding on my babe again XD~ ty

---

