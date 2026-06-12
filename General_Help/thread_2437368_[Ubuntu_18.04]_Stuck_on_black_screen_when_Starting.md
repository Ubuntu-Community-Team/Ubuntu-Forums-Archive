---
title: "[Ubuntu 18.04] Stuck on black screen when Starting Ubuntu (booting) after upgrade."
date: 2020-02-22
forum: General Help
---

### Post by jsimancas on 2020-02-22
[COLOR=#1A1A1B][FONT=&amp]Hello EveryOne, i have a problema and i wish i could find some help, please:[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]i installed ubuntu 18.04 in my laptop, and it was working good, but recently i did an apt upgrade and needed to restart, and now Ubuntu is not starting becouse it gets stuck on a Black Screen, i dont know why :([/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]i only can start ubuntu through recovery mode.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]My laptop is a AMD Ryzen 3 3200U, and my kernel is 5.3.0-40-generic. I hope someone can help me. please[/FONT][/COLOR]

---

### Post by ajgreeny on 2020-02-22
Did your upgrade install a new graphics driver or kernel version which may have caused your problem?
Using Recovery mode if necessary run terminal commands ```
ls /boot | grep vmlinuz
uname -a
```
This will tell us which kernels are currently installed and available and then the kernel actually in use, and if more than one is available try booting to the older version from the Grub menu at next boot.
Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. 
See my signature below for a **How-to**

---

### Post by jsimancas on 2020-02-22
This worked! thank you.

i did the commands in the terminal, and it shows:

vmlinuz-5.0.0-23-generic
vmlinuz-5.3.0-40-generic

the 5.3 kernel has the problem for my laptop, i switched back to kernel 5.0 and it worked fine. 

i just found a way to make kernel 5.0 the default one when booting in here: [Set a default kernel]("https://unix.stackexchange.com/questions/198003/set-default-kernel-in-grub")

thank you very much for helping me @ajgreeny!

---

