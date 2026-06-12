---
title: "Passwords and upgrading/updating the OS"
date: 2020-07-09
forum: General Help
---

### Post by jimgood70+ on 2020-07-09
Greetings,
Yes, it seems that I have a few problems with my computer.  First, the computer is a Dell Inspiron-3268 and has a 1 TB internal hard drive.  Up until about 18 months ago, this computer was operating with Windows 10.  Then Windows informed me that an 'update/upgrade' needed to be done.  One step in that update/upgrade included a restart.  As the computer restarted, a screen came up telling me to 'log in' and enter my log-in account name and password.  I entered the username and password that was being used for my email account.  That information was wrong.  I reentered the information and again was informed that I had entered information that was incorrect.  At that point, and after becoming thoroughly disgusted with everything Microsoft, I grabbed a DVD that I had earlier burned an ISO of Ubuntu Linux on and booted that.  At first (about a week) I used a dual boot system.  Then I did a full install of the Linux Operating System.  The original passwords were saved both to the computer and to a paper log in the event anything happened to the computer copy.  All of the software updates and upgrades were completed without any problem.  Until earlier this year.  Sometime in the first month or two of 2020, any time I tried to enter a terminal command that required the 'sudo' password, that password would fail.  Somewhere I had found a way to reset the passwords (root, user, and all others) and tried to follow those instructions.  However, those efforts seem to also be failing.  Today, I attempted to upgrade the operating system from 18.04.4 LTS to 20.0+ or the most current LTS version.  Again, the computer wanted the password, which was entered, and which again failed.  Basic problem; I need to regain total control of the computer and all passwords used on it so that I can learn more about Ubuntu and the Linux Operating System and language.  Until the time of the switch from the Windows operating system to Linux, I had mostly been a 'computer user' that enjoyed many of what was offered through the Windows OS.  Please help.  Thank you,
James Good

---

### Post by Impavidus on 2020-07-09
There's only one password important to Ubuntu: your login password. If you loose it, it can't be recovered, but it can be reset: [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
You may have seen that link already.

You can configure your computer to allow login without the password, but that's not really recommended. It's less secure and you're more likely to forget if you don't type your password a few times every day. And there have been some problems with passwordless login in the past, making login fail.

There may be a second password important to Ubuntu if you encrypted your hard drive, but that doesn't appear to be the case here. In that case, you have to enter the password every time you boot. There's no root password (unless you really want, but that's not recommended). All other passwords (e-mail, logins on websites, ...) are irrelevant to Ubuntu. I assume it's the same on Windows, but I don't use Windows.

Can you type your password in a text editor or something like that? Does it look OK? Just to rule out a keyboard problem.

---

### Post by crip720 on 2020-07-09
It is quite odd for two operating systems on same computer to both lose access to login passwords.  Do you notice any other problems?   As Impavidus asked is keyboard not wonky, would try another keyboard before doing anything else making sure you type in correct password, use your paper copy to be sure.  Can also try changing how keyboard is connected to computer, if possible, different USP port.

---

