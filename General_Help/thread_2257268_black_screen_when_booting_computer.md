---
title: "black screen when booting computer"
date: 2014-12-18
forum: General Help
---

### Post by Totolanio on 2014-12-18
Hello,

Lubuntu 14.04

When I start my computer, after the GRUB menu, it's a black screen.
It already happened to me several times but I could always restart the computer and it worked.

Yesterday, SUDDENLY (no update occured at the same time), my skype got closed and couldn't open it back because there was an error and it worked with sudo skype (so a permission error). I couldn't also open images and watch them.

Today, I start the computer and black screen. I tried many things and here are my results :

1 - used "nomodeset" and it changed NOTHING
**2 - used "nomodeset" and "xforcevesa" and the login screen appeared (which is not normal) and I couldn't log in, it constantly brought me back to the login panel**
3 - tried apt-get update, upgrade etc but couldn't download some packages (and nothing to install)
4 - tried dpkg-reconfigure xserver-xorg = did nothing. Same for "dpkg --configure -a"
5 - tried ctrl +alt + f7 (nothing showed, only when I used xforcevesa)
6 - tried ctrl + alt + f1 and typed "startx" but there was an error message saying : "Waiting for X server to begin accepting connections  : no protocol specified (infinite loop"
7 - removed .Xauthority when using xforcevesa but it didn't change anything
8 - Do i have to do these things [https://community.bitnami.com/t/errors-starting-ubuntu-desktop-on-drupal-7-stack/8997/2](https://community.bitnami.com/t/errors-starting-ubuntu-desktop-on-drupal-7-stack/8997/2) ? clean, autoremove, isn't it risky ?

Please, someone help me before I have to reinstall everything

---

### Post by Totolanio on 2014-12-18
Up :(

---

### Post by QIII on 2014-12-18
Hello!

We know that this is an important issue to you, but remember that the community is world-wide and its members reside in all time zones.  4 hours of your time represents about 1/6 of the potential number of those who could help.

Although we have relaxed the 24 hour bump rule, 4 hours is a bit too hasty.

Consider also that by bumping your thread you have made it so that it will no longer appear in the "unanswered threads" query many people use first thing when they log in to help.

Please be patient and let the community work.

Thanks.

---

### Post by Totolanio on 2014-12-18
Ah ok, sorry and didn't even know about the unanswered threads.
I just saw my thread was already page 2 and since I can't use my computer, it's a bit worrying.

Now I want it to have 0 answers back :D

---

### Post by Totolanio on 2014-12-19
Hello,

Lubuntu 14.04

When I start my computer, after the GRUB menu, it's a black screen.
It already happened to me several times but I could always restart the computer and it worked.

Yesterday, SUDDENLY (no update occured at the same time), my skype got  closed and couldn't open it back because there was an error and it  worked with sudo skype (so a permission error). I couldn't also open  images and watch them.

Today, I start the computer and black screen. I tried many things and here are my results :

1 - used "nomodeset" and it changed NOTHING
**2 - used "nomodeset" and "xforcevesa" and the login screen  appeared (which is not normal) and I couldn't log in, it constantly  brought me back to the login panel**
3 - tried apt-get update, upgrade etc but couldn't download some packages (and nothing to install)
4 - tried dpkg-reconfigure xserver-xorg = did nothing. Same for "dpkg --configure -a"
5 - tried ctrl +alt + f7 (nothing showed, only when I used xforcevesa)
6 - tried ctrl + alt + f1 and typed "startx" but there was an error  message saying : "Waiting for X server to begin accepting connections  :  no protocol specified (infinite loop"
7 - removed .Xauthority when using xforcevesa but it didn't change anything
8 - Do i have to do these things [https://community.bitnami.com/t/errors-starting-ubuntu-desktop-on-drupal-7-stack/8997/2](https://community.bitnami.com/t/errors-starting-ubuntu-desktop-on-drupal-7-stack/8997/2) ? clean, autoremove, isn't it risky ?

Please, someone help me before I have to reinstall everything

---

### Post by lisati on 2014-12-19
Threads merged.

---

### Post by agillator on 2014-12-19
I can't speak for Lubuntu, but for xubuntu the blank screen after Grub is normal until just before the xubuntu/login screens. It can actually seem to last a long time. If that is the problem the solution is relatively simple. Go ahead and boot, be patient. When booted and logged in, edit the file /etc/default/grub. Edit the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" to remove the 'quiet'. Actually, copy the line, put a # in front of the original and edit the copy. Then update-grub. When done, reboot. Instead of a long black screen you should now get output from the commands scroll by. They may not mean anything to you, but at least you will know that the boot process is continuing. If something does fail, it will help you determine what and why. Do remember it may take a few seconds for some of the start-up programs to run, so it may appear to hang occasionally.

---

### Post by Totolanio on 2014-12-20
I don't say thank you for merging threads, that was not very smart. I shouldn't have report it i guess and let my first thread flood the forum.

Agillator, thank you for trying!!! but I use Lubuntu for 1 year and that's not normal. I restarted hundred times, I mentionned I tried to solve the problem so it's not like I instantly came here asking for help ! I also let it run during 1h and nothing showed. It stayed BLACK forever.

I already used these things to debug at boot, and there is only one thing failing, it's about SMB/CIFS directory but I don't know what it is. 
However the problem is about the X server.

I guess i'm doomed and I must reinstall.

---

