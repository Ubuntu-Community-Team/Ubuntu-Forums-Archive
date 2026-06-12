---
title: "Password does not work in Ubuntu 18.04"
date: 2019-01-23
forum: General Help
---

### Post by mountainman70 on 2019-01-23
I wanted to change my signin password in Ubuntu 18.04. I thought it was time for security reasons. I tried command line in the terminal  but it would not accept my password so I tried other passwords and it would not accept any of them. I then tried the graphical user interface but it won't accept password. How do I find my password I can signin with the terminal? Also I must say that when I turn on the computer Ubuntu boots up fine. I am running dual boot w10 & Ubuntu 18.04. Thanks for any help.
[h=3][/h]

---

### Post by QIII on 2019-01-23
Hello!

Would you cut and paste the command you are issuing in the terminal and the output received?

---

### Post by mountainman70 on 2019-01-23
> **QIII said:**
> Hello!

Would you cut and paste the command you are issuing in the terminal and the output received?

I am using the way it is posted here ([https://linuxconfig.org/how-to-change-password-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-change-password-on-ubuntu-18-04-bionic-beaver-linux)). I can't get passed current password. It will not accept what I put in.

---

### Post by QIII on 2019-01-23
What do you mean it will not accept what you put in?

Please post exactly what commands *you* are issuing and the output of those commands.

---

### Post by HermanAB on 2019-01-24
Looking at that tutorial for the passwd command - are you perchance typing the $ also?  

The $ is a prompt.  Don't type it.  The command is passwd only.

---

### Post by mountainman70 on 2019-01-24
> **HermanAB said:**
> Looking at that tutorial for the passwd command - are you perchance typing the $ also?  

The $ is a prompt.  Don't type it.  The command is passwd only.

Thank you for replying. I do not use the $, just copy & paste. I have searched & tried several different ways to change password. If I want to install something using terminal I enter password & it says the password is invalid or wrong password.Same thing if I use  the graphical user interface. Don't understand why everything that asked for a password would say invalid or wrong. It could only be one of two passwords neither of which work.

 I finally got tired  of fooling with it and just wiped Ubuntu and did a clean install.  Now everything is back to normal.

Thanks everyone who replied.

---

### Post by mountainman70 on 2019-01-28
Well it looks like I spoke too soon. After installing ubuntu 18.04 on this Dell xps 8900 with W10 and installing all my programs it says I am running out of space. Gparted shows ubuntu partition as way over half as unused. Uninstalled ubuntu & re-installed & get the same thing. Wiped hd with gparted, formatted to ntfs & re-installed W10. Now when I try to install ubuntu 18.04 I get this: ubi partman failed with exit code 10. Tried a search but do not understand exactly how or what to do to correct this. Both W10 & Ubuntu 18.04 flash drives have been used on other computers with no problems. Only problem is on this xps 8900.

---

