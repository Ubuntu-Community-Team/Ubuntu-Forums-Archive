---
title: "I screwed something up badly, how do I start finding the problem to fix"
date: 2013-09-20
forum: General Help
---

### Post by Dospanes on 2013-09-20
Hello friends, 

 I'm quite new to Ubuntu and did something maybe  every new Linux user does at the beginning. I screwed up something badly  and now the whole system is troubeling me.   I don't now how to  check my system in order to find what the problem is. Is there some  standart procedure? I try to reconstruct what I did in order to minimize  the possible options. 

  So it all started when I tried to Install  Crossover Trial with the Ubuntu Software Center yesterday morning.  Somehow the programm couldn't finish installing. It hung up at around  80% and my CPU was going crazy. After about 20 min and my laptop was  really getting too hot, I killed the programm via terminal and rebootet  Ubuntu. To my surprise I could find the programms icon and I could start  the programm but since it wasn't working properly I deinstalled it  again via the Ubuntu software center (bad mistake) and again, it hung up  at arround 70%. CPU was going crazy again so I had to kill it again.   After  that a lot of programms went crazy (allmost all hung up when I tried to  open them). 

I think the system was espeacially complaining about  Phyton libraries. So I downloaded Ubuntu tweak and cleanded up with the  janitor and then I did some software updates and upgrades.   After  that my ubuntu seemed to work properly but today problems started  again. Firefox hangs up, homepages are displayed strangly, in  Thunderbird  the folders get mixed up, the statistical Software R  won't start, neither PGadmin and others. QGIS tells me that it can't load the Phyton libraries. The owncloud client sometimes works sometimes not (as with other programms too). Most programms seem to work only after a while and several attemps to open them. 


  So how do I start searching for the error to fix it? Any help would be very appreciated. Thx

---

### Post by coldraven on 2013-09-20
I've never tried this but dpkg might help you.
From the dpkg manual:
"-C, --audit
              Searches for packages that have been installed only partially on your system. dpkg will suggest what to do with them to get them working."

Try running this in a terminal and see what it suggests.
```
sudo dpkg --audit
```

---

### Post by Dospanes on 2013-09-20
> **coldraven said:**
> I've never tried this but dpkg might help you. From the dpkg manual: "-C, --audit               Searches for packages that have been installed only partially on your system. dpkg will suggest what to do with them to get them working."  Try running this in a terminal and see what it suggests. ```
sudo dpkg --audit
```    Thanks for the advice. Brings no result...

---

### Post by CatKiller on 2013-09-20
It sounds to me that your initial problem was caused by an unrelated hardware fault; I would suspect hard drive or RAM. That caused the installation process to get into a bad state, and your ongoing problems. A failed installation of one package will not affect previously-installed packages at all.

Memtest is available from your GRUB menu, and there are diagnostics you can run on your hard drive.

Walls of text are hard to read.

---

### Post by Dospanes on 2013-09-20
> **CatKiller said:**
> It sounds to me that your initial problem was caused by an unrelated hardware fault; I would suspect hard drive or RAM. That caused the installation process to get into a bad state, and your ongoing problems. A failed installation of one package will not affect previously-installed packages at all.

Memtest is available from your GRUB menu, and there are diagnostics you can run on your hard drive.

Walls of text are hard to read.

I guess it was not a hardware problem because i used Ubuntu for three weeks without any trouble at all. But the information about failed installations was usefull to me (didnt had to pay  much more attention to this).

After that I look up the Disk Usage Analyzer and saw that the partition linux is installed on was nearly a 100% full. So I guessed that this may cause some troubles and after freeing some space by moving the /home directory to another partition bingo! All programms are (until now) working fluently. 

Strange behavior though in my opinion. Never seen that on another OS that programs actually stop working when the disc is full...

---

### Post by CatKiller on 2013-09-20
I personally count a full partition as a hard drive problem ;)

Glad you got it sorted.

---

### Post by Dospanes on 2013-09-22
> **CatKiller said:**
> I personally count a full partition as a hard drive problem ;)

Kind of true :) thanks for the help!

---

