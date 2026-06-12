---
title: "Can't open items on the launcher"
date: 2012-12-03
forum: General Help
---

### Post by LyTningB0LT on 2012-12-03
I'm new to Ubuntu and Linux so I apologize in advance if this is a stupid question.  I installed ubuntu 12.10 on my 8GB USB drive, which I formatted as FAT32, using Universal USB Installer from pendrivelinux.com, and gave it 4GB of persistence.

I booted it up, experimented with a few things, installed ubuntu restricted extras, and everything seemed to be working fine.  But then I tried to open the dvd I had in my dvd-rom drive, and it simply won't open.  I click the icon on the launcher and nothing happens.  I'm getting the same result when I click on casper-rw, system, and os.  I tried ejecting the dvd and reinserting it, and I get the following error:

> Unable to mount (dvd name)
Adding read ACL for uid 999 to `/media/ubuntu' failed: Operation not supported

What's going on?  Thanks in advance for the help.

---

### Post by ibjsb4 on 2012-12-03
Hi LyTningBOLT, welcome to the forum  :)

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=play+dvd&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=play+dvd&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by LyTningB0LT on 2012-12-03
I have ubuntu-restricted-extras and libdvdcss2 installed, and I'm still having the same problem.  I don't know if it's directly DVD related, because I get the same error when trying to open the System, OS, and casper-rw folders.

And thanks :)

---

### Post by LyTningB0LT on 2012-12-04
Apparently /media/ubuntu did not exist, which was causing my problems.  I created it manually and now everything seems fine.

---

### Post by 3rdalbum on 2012-12-04
> **LyTningB0LT said:**
> Apparently /media/ubuntu did not exist, which was causing my problems.  I created it manually and now everything seems fine.

I'm glad you sorted it out, I ran into the same bug when installing 12.10 on my father's computer. It seems like a rather visible bug, I'm surprised it wasn't picked up earlier, but I can't really complain too much as I didn't help test before release.

---

