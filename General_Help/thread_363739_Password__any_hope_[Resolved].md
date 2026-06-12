---
title: "Password : any hope? [Resolved]"
date: 2007-02-17
forum: General Help
---

### Post by shankariyer on 2007-02-17
Ok, I did the stupid thing. Forgot my password. Had created only one account, but forgot its password.

Anything can be done now or re-install ?

:(

Kramer.

---

### Post by taurus on 2007-02-17
Boot into recovery mode from GRUB menu and change the password.

```
passwd **shankariyer**
shutdown -r now
```
Assuming **shankariyer** is your login name.

---

### Post by mcduck on 2007-02-17
No problem:

1. boot into recovery mode (select the option in Grub menu).This will log you in text mode as root.
2. run 'ls /home'to check thast you got the right username (this will list all normal uesrs, as they all have their own home directories in /home.
3. run 'passwd <username>' (replace <username> with your usename. This will let you set new password.
4. 'reboot' will restart the computer, and now you should be able to log in again.

edit: too slow :(

But as these threads usually end with somebody complaining how unsafe this is, I'll answer that before you ask about it:

As long as somebody gets physical access to your computer it's never safe. Simply by inserting a live-cd into drive and booting with it will give full access to your system. And hard drives can alway be moved to another machine to get access to your data. BIOS password can be cleared by removing CMOS battery or using reset jumpers on the motherboard (and some laptops even have small reset button in bottom). Having the recovery mode in grub menu makes no difference, but it's possible to set password protection for Grub menu if that makes you feel warm and fuzzy and safe.

---

### Post by shankariyer on 2007-02-17
You guys rock! Ubuntu and its support process such as this really really rocks!

Thanks !

---

