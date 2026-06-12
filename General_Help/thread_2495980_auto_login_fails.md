---
title: "auto login fails"
date: 2024-03-10
forum: General Help
---

### Post by VMC on 2024-03-10
I've installed several Xubuntu's [Nobel, LTS]. All fail to log in automatically. The log in auto was selected on first install.
Researched, and tried all the fixes know to man. Mostly editing LightDM config files. Tried all of them. Failed
journal has some tell tale errors. Usually after giving my pasword on powerup, I can reboot and it doesn't require password.

This is the odd part. ONLY Xubuntu does this. I've tried a dozen other XFCE distros. All of them auto login as expected.
Ubuntu and Mate which I'm now using works without an issue.

I'm beginning to think its my PC. I have a Gateway laptop with Xubuntu installed. It works without issue.

I can get Xubuntu to boot without password using the XINIT method. But that is slow to boot.

---

### Post by #&amp;thj^% on 2024-03-10
A few things to try, this was a problem in 20.04 as well btw.
Disable splash from /etc/default/grub (+update-grub).

create a new 'testuser' and set Autologin on that user.
confirm that Autologin worked for testuser.
remove Autologin from testuser and turn it back on for your user.

Hopefully that still works on Noble

---

### Post by VMC on 2024-03-10
Thanks for reply 1fallen!

---

### Post by VMC on 2024-03-22
Solved by using this [guide]("https://forums.debian.net/viewtopic.php?t=123694") from Head-on-a-Stick. Tried other DM'less methods, but they just didn't work correctly.

---

