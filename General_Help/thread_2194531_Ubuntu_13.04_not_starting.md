---
title: "Ubuntu 13.04 not starting"
date: 2013-12-19
forum: General Help
---

### Post by aanchal.arora175 on 2013-12-19
I have ubuntu 13.04 installed in my system. I was installing gtk+, which has many dependencies, so I installed all of them. At some point, an installation said that there are unmet dependencies, so try apt-get -f install. I ran this command and then turned off the system. After that, when I m trying to start the system, it gets stuck up at the loading screen. Nothing happens. What I can I do? Thanks in advance.

---

### Post by entw on 2013-12-19
1) ctr+alt+f1
2) log-in
3) connect to the internet if not connected
4) sudo apt-get update
5) sudo apt-get dist-upgrade

If you're not able to log-in after switching to virtual terminal (steps 1, 2) then boot into [recovery mode]("https://wiki.ubuntu.com/RecoveryMode") (press Shift before bootsplash shows up and select recovery mode in "Advanced boot" ? menu) then run dpkg (Package management - one of the menu options).

---

### Post by aanchal.arora175 on 2013-12-21
Thanks entw for your reply. I tried both the options but nothing happened. Again it got stuck at loading screen.

---

### Post by mörgæs on 2013-12-21
13.04 has only one month of support left. Have you considered a clean install of 13.10?

---

### Post by JohnMac on 2013-12-21
I seem to have the same problem with Ubuntu 12.04. I tried starting with in the advanced mode and then booted with the previous version. This at least got me into my desktop, with chunky graphics though. I shall try doing a distro update as entw advised.

Good luck

---

### Post by Crossbow on 2013-12-21
I have 3.10 but I can't use it due to all the GTK errors. I don't even know what they mean.

---

### Post by JohnMac on 2013-12-21
entw's advice did not work for me. At least I have a desktop to work on.

---

### Post by JohnMac on 2013-12-23
I loaded Lubuntu and it is working fine. I can't explain my Unity 12.04 doesn't work as it should, One day it was working at 1680 x 1050, I did a kernal update and next time I started,  I had to go back to my previous kernal and even then I was limited to 800 x 600. I like my Unity so I'll have to try and nut it out.

---

### Post by aanchal.arora175 on 2013-12-24
JohnMac, how can we start the advanced mode?

---

### Post by aanchal.arora175 on 2013-12-24
No morgaes, I did not try to install 13.10. Actually I have some data in ubuntu 13.04, which is not accessible through windows, so I want to log into that only.

---

### Post by JohnMac on 2013-12-25
Do you get a menulist when you first boot? One of the options I get is to boot "advanced options for Ubuntu ...."  If that is not available, do you have a Boot Repair Disk? With that you can do many handy fixs including "Reinstall latest kernal"

---

