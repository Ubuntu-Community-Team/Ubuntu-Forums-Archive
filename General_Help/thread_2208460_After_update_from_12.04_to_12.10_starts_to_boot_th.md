---
title: "After update from 12.04 to 12.10 starts to boot then black screen and no more."
date: 2014-02-28
forum: General Help
---

### Post by mmcl26554 on 2014-02-28
I upgraded from 12.04 to 12.10 and planned to keep doing this until I get to 13.10.   However, the first upgrade seems to have failed now all that happens is it starts with a black and white Ubuntu logo then the screen goes black and there is no more hard drive activity.   I can use recovery and get to a terminal login screen, which asks for my username and password.   Then I am where I would be if I brought up the terminal.   I am not experienced enough with Ubuntu to know what to do next.   Since I do have a backup of the two Linux partitions (/) and swap I can restore.   But, since I am in learning mode with Ubuntu and have no data to lose, just a lot of programs and settings, I am not in any distress.   I would like to fix this and go on to the other upgrades.    I have a usb live of trusty and it boots the computer fine.     The computer is an HP Pavilion G6 and is only about 9 months old.   So can someone tell me where I go from here.   Please remember I am a beginner.
Michael

---

### Post by jeanjd63 on 2014-02-28
Hello

On black screen can you open a console (CTRL+ALT+F1)
If yes try :
[B]startx
[/B]and give returns

---

### Post by mmcl26554 on 2014-02-28
Once it gets to the black screen no key works.   However, I am able to get into recovery and then get to the terminal where I did enter "startx".  It ran through a lot of entries and this are the ending ones:```
Fatal server error no screens found
please consult the x.org foundation support at wiki.x.org
(EE) please also check the log at /var/log/xom.O.log
server terminated with error (1) closing log file
Xinit:giving up
Xinit:unable to connect to X server: connection refused
Xinit: server error
```

What does this all mean?
Michael

---

### Post by jeanjd63 on 2014-02-28
What return :
**sudo  lspci -vnn |  grep  -i  vga**

---

### Post by mmcl26554 on 2014-02-28
I went into recovery mode and got to the counsel where I can enter the code  lspci -vnn | grep -i vga and I got the following:
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd generation Core Processor family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])

---

### Post by jeanjd63 on 2014-03-01
In recovery mode (root), connected in ethernet, you can try :
[B]mount -o  remount,rw  /
sudo  apt-get  update
sudo  apt-get  dist-upgrade[/B]

---

### Post by mmcl26554 on 2014-03-01
I finally gave up on this as it was to much work to try to fix it.   But things got even worse when I tried to install 13.10 from a USB stick.   For some reason Grub got really messed up and boot repair had me connect to the internet to fix it.   Ultimately that got fixed but now Ubuntu won't shutdown properly, when I click on shutdown it clears everything from the screen except the cursor which still will move with the mouse and the screen remains blank with nothing on it.   I am going to uninstall ubuntu and remove it partitions and clean the mbr and try again.   If that doesn't work I'll just go to a full backup of the hard drive which is only a few days old and reinstall everything and give up on 13.10.
Michael

---

