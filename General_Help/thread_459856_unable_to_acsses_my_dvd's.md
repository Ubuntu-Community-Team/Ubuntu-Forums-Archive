---
title: "unable to acsses my dvd's"
date: 2007-05-31
forum: General Help
---

### Post by Firminator on 2007-05-31
Hello, I have upgraded from 6.10 to 7.04(bothe are running the gnome desktop) and  since then, I can't read any of the dvd's I Have burned on Win XP using Nero. while I was runing the Ubuntu 6.10 i was able to read them. I'm totally clueless can anyone help me please?

---

### Post by MoLE on 2007-06-07
Do other discs work?  Eg: pressed CDs, DVDs, other DVDs burned in ubuntu?

---

### Post by quasi_71 on 2007-06-08
Same problem here. I have a Dell GX150 running Ubuntu Feisty. I removed the cd-rom drive and replaced it with a dvd reader/cd writer combo drive. I can read CDs but for some reason can't write and am completely unable to see any files on dvd media. The drive works fine in other operating systems. I tested it just now with Geexbox and it played a dvd movie flawlessly. I also have 2 drive icons....... help !

---

### Post by mdurham on 2007-06-08
There are many bug reports of CD/DVDs not working correctly, it's strange that the devs haven't done anything about it!
My solution was to abandon Feisty and upgrade to Gutsy which, with the latest kernel, seems to work okay. I don't know if that's an option for you. Gutsy could be (and sometimes is) a bit unstable.
Cheers, Mike

---

### Post by MoLE on 2007-06-08
If you post your /etc/fstab file as an attachment here, it may help.  If you open System --> Preferences --> Hardware information, what capabilities are listed by the drive?

---

### Post by MoLE on 2007-06-08
.

---

### Post by quasi_71 on 2007-06-08
Got it fixed... not sure which of the following things actually did the trick though......
1- Installed Automatix
2- Installed DVD codecs (AUD-DVD) ?
3- Allowed an automatic update to install (mentioned something about HAL)
4- Rebooted

---

### Post by ming0 on 2007-06-09
bummer, the Automatix trick didn't work for me (although it did have some HAL related upgrades for me after I did it).

---

