---
title: "Two Different Wubi Installs?"
date: 2007-07-05
forum: General Help
---

### Post by mschraier on 2007-07-05
A few wekks ago I installed using Wbui that I downloaded from their site.  It worked no problem, even found my WiFi card.  HOwever , I unisntalled it and decided yesterday that I wanted it again.  This time I using this link [http://sourceforge.net/project/showfiles.php?group_id=198355](http://sourceforge.net/project/showfiles.php?group_id=198355).  Upon install this time, it asked where I wanted to install and so forth.  The insgtall went perfectly.   It did find my WiFi cared when I inputted my WEP settings I was unable to connect to the net.  I use a D-Link WI-624 wireless router and an Intel PROset Wirless 3945abg intemal in my Dell Inspiron E1505.  Why would this new install give me such an issue with the net?  I tired DCHP and manually setting the IP an so forth.  No matter what the scenario, the WiFi LED was lit but could not connect.  I dont want to go back to the older install because I like the fac that the new one allowed me to specify a partition already existing on my drive.

As a side question.  I do have the install Cd that I received from Ubuntu.  My hardrive, as I stated before, has a "D" partition of 11GB.  If i use the regualr install CD, does the install process give me the optionj of choosing this dirve?  If so, will it automatically create a dual boot with XP?

---

### Post by ago on 2007-07-05
> **mschraier said:**
> 
As a side question.  I do have the install Cd that I received from Ubuntu.  My hardrive, as I stated before, has a "D" partition of 11GB.  If i use the regualr install CD, does the install process give me the optionj of choosing this dirve?  If so, will it automatically create a dual boot with XP?

My simple suggestion is: if you have tested Ubuntu via wubi and you like what you see and you have a spare partition drive, by all means use the standard installation. Yes you wil be able to select the partition/drive on which to install, and yes it will configure the dual boot automatically.

As for the network card that is unlikely to have much to do with wubi.

---

### Post by mschraier on 2007-07-05
u are aware of the two diff Wubi version i have mentioned, i am sure.  i just cannot understand if the version of Ubuntu it accesed each time was the same, that now thw wifi is out?  although the first i did it, it defau lted to install on the C drive.  Would that make a diff?

---

### Post by mschraier on 2007-07-06
I tried the standard install and when it was time for the partion questions, i had no clue if i had to format to ext or nefis or whatever it is called.  However, it makes no diff now.  The HD is toast.  blue screen for HD corruptiuon.  No capability of anything even safe mode.  tried booting with install cd. as soon as it would go to hceck hardware config. the screen would go black and the HD light would stay lit.  i think i am gonna let Linux mature just a bit more and give it another try.

---

### Post by ago on 2007-07-08
> **mschraier said:**
>  The HD is toast.  blue screen for HD corruptiuon.  No capability of anything even safe mode.  tried booting with install cd. as soon as it would go to hceck hardware config. the screen would go black and the HD light would stay lit.  i think i am gonna let Linux mature just a bit more and give it another try.

That's probably a wrong configuration rather than a problem of linux maturity, the standard installer is quite well tested (it has been used by several million users). Anyway you should be able to use the Live CD itself to recover any file/retry the installation. The easiest and safest way is to have a part of the disk (or even better a second hd) completely free. And let the installer use the available space automatically.

---

### Post by Romanus81 on 2007-07-09
I have your same router, and the same thing happened to me. I once broke ubuntu and downloaded the newest Wubi and had to redownload the iso. I'm not quite sure how I got it working, but I think I just typed in the WEP key, closed the manager. Reopened the network manager, and then at the bottom it said "starting network connections" or something like that. Afterward it might have worked, or I think I might have restarted the computer, or at least the X session (ctrl + alt + backspace)

---

