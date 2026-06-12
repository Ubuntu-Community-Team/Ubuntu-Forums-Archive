---
title: "X.org not working, please help!"
date: 2008-05-03
forum: General Help
---

### Post by GregMB on 2008-05-03
Hi. I am using Ubuntu Gutsy, and I'm having a problem with xorg.conf. About five minutes ago, I uncommented the lines in xorg.conf about a Wacom Tablet, because it said to do so if you have a wacom tablet. Sounds simple enough? Not so. After I did that, I pressed Control-Alt-Del to restart X. I had never done this before, so I didn't know what to expect. It gave me three scary messages about X, all with [OK] at the end. The last one was something about scripts or something, and seemed to be taking a while. Now, I normally don't do anything at all like this in Ubuntu, because it seems like there's nothing I can do without breaking anything, but I /really/ want my tablet to work. So anyways, after that it said X couldn't be started, because it was too long or something. So here's my question: If I were to go in with VIM and re-comment those three lines, it will fix it, right? Also, what command should I use to do that? And yes, I learned my lesson. If it ain't broke, don't fix it.

---

### Post by macaholic on 2008-05-03
Ya, you can go into a tty terminal, (ctrl + alt +  Fnumber), login and type:```
sudo vim /etc/X11/xorg.conf
```

---

### Post by Dr Small on 2008-05-03
Look on the bright side, if you break it, Ubuntu let's you keep both pieces :)

Open a Virtual Terminal (CTRL + ALT + F1)
Login, then run:
```
sudo vim /etc/X11/xorg.conf
```

You should be able to fix your problem from there.

Dr Small

---

### Post by GregMB on 2008-05-03
Thank you so much, I'll try that right now. Because I have wiped my hard drive twice, I'm afraid that every little thing I do will cause my computer to explode.

---

### Post by GregMB on 2008-05-03
Sorry, two last things I need to know before I do this: One, after I recomment those lines, then what? Second, if this doesn't work, the worst that will happen is that X doesn't work, right? My computer won't become a piece of large charcoal?

---

### Post by Dr Small on 2008-05-03
After you recomment the lines, save the file, and try going back to VirtualTerminal 7 (CTRL + ALT + F7) and pressing CTRL + ALT + SHIFT + BCKSPC to try to restart Xorg again.

If all else fails, reconfigure xserver-xorg.
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by GregMB on 2008-05-03
Well, Thank you very, very much. Unfortunately, I probably won't try those commands until tomorrow, but luckily I dual-boot Windows and Ubuntu, so I have a backup. Dual-booting has saved me from catastrophe so many times I can't even begin to count them.

---

### Post by Dr Small on 2008-05-03
Don't let things like this bother you. Just simply make backup files, and when something goes wrong, use the backup. Never let the fear of the unknown (or breaking something) stop you. :)

---

### Post by GregMB on 2008-05-04
First off, let me say how much you helped me. THANK YOU VERY MUCH!

> **Dr Small said:**
> Never let the fear of the unknown (or breaking something) stop you. :)

Well, I don't really have anything on my computer important enough to backup, except I dual-boot with XP and I lost the XP install disc. If I destroy my computer, I will have to fork over $200+ over so i can have a lousy backup OS on my computer (I have some Microsloth Window$ only programs I need.). Also, I've become afraid of installing OSes after I switched to Ubuntu. xD Anyways, THANK YOU!

---

