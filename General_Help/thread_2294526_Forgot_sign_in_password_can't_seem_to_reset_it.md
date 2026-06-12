---
title: "Forgot sign in password can't seem to reset it"
date: 2015-09-11
forum: General Help
---

### Post by jdbic on 2015-09-11
Forgot the password. Searched and read all things to try. I can't get to the menu to get to rescue. I hold shift, grub loading pops on screen, blink and its gone. If I reinstall will the files I have stay? I have lubuntu 14.04

---

### Post by Bashing-om on 2015-09-11
jdbic; Hello;

A (RE-)install is not advocated. ubuntu is fixable - given time, effort and a liveDVD.

So, not getting the grub boot menu. ?
Is this system UEFI endowed ? - then it is the escape key that grub looks for to enable activating the grub boot menu.

Here are easy instructions to reset your password in Ubuntu:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by jdbic on 2015-09-11
OK, thank you for helping me out. Still can't get to that menu. Esc doesn't do it . I end up at my bios page. But good news! I found the password. But what makes the grub loading pop up and go away and go right into booting lubuntu?

---

### Post by Bashing-om on 2015-09-11
jdbic; Hey, progress made .

Take a look on the control file ' /etc/default/grub ' .
What is set for the " GRUB_TIMEOUT " ?

What is and how to: A good place to start:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

If ya post the file, we can examine and make recommendations .

[INDENT][INDENT]maybe
[INDENT][INDENT][INDENT]just doing as it is told
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

