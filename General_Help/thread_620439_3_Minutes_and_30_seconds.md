---
title: "3 Minutes and 30 seconds"
date: 2007-11-22
forum: General Help
---

### Post by nami on 2007-11-22
From the time I press the start button to the time it takes to see the login screen, it takes 3 minutes and 30 seconds...  While it is loading, I don't see any message saying that it is loading, and I don't see the progress bar either.

I have P4 1.7GHz with 768Mb Ram.

Why is it taking so long to load up?

Once it reaches the login screen, everything is nice and fast...

---

### Post by handaxe on 2007-11-22
Have you tried the bootchart package?

Should show wots wot.  In fact, I am going to try it myself.

My system seems to slow down at the fscks of my partitions...

HA

---

### Post by Kris da Kiwi on 2007-11-22
Hi
I have a P4 2ghz and it to is slow.
To help speed it up I altered the menu.lst and removed the splash .
that seemed to make a big difference

---

### Post by nami on 2007-11-23
I did a fresh install not to long ago, when gutsy gibbon came out.  the boot time was good, but then a few days later the loading screen disappeared and it is now taking 3 minutes 30 seconds to load...

---

### Post by misfitpierce on 2007-11-23
No progress bar showing loading and such sounds like bootsplash not going right. You can always hit escape on grub thing to see partitions and on main one edit it so splash is nosplash then hit enter and see how it boots. If it boots faster find way to set permanantly I forgot exact command.

---

### Post by ugm6hr on 2007-11-23
[http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

Same problem as you (and me) - solution in Post 2

---

### Post by nami on 2007-11-23
Thanks for the help everyone.

I will try this when I get home tonight.

---

### Post by nami on 2007-11-23
> **ugm6hr said:**
> [http://ubuntuforums.org/showthread.php?t=581075](http://ubuntuforums.org/showthread.php?t=581075)

Same problem as you (and me) - solution in Post 2

That fixed the problem!  I timed it again and this time it took 1 minute and 15 seconds from the time I pressed the power button to the time it displayed the login screen.

Thanks for that.

Is it possible to make it faster?

---

### Post by KIAaze on 2007-11-23
Compile everything you need from source with optimization flags. ^^

It seems Gentoo and Slackware are some of the fastest distros because of that.
DSL is said to boot in 6 seconds.

Some quick results from google:
[http://www.improvedsource.com/view.php/linux-system/2/](http://www.improvedsource.com/view.php/linux-system/2/)
[http://www.linuxquestions.org/questions/linux-desktop-74/linux-distro-with-the-fastest-boot-598972/](http://www.linuxquestions.org/questions/linux-desktop-74/linux-distro-with-the-fastest-boot-598972/)

I don't know for Ubuntu, but I suppose this thing drawing boot charts can help speed up boot...
> sudo apt-get install bootchart

The easiest is probably to disable services at startup you don't need.

---

