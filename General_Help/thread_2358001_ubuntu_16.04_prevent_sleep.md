---
title: "ubuntu 16.04 prevent sleep"
date: 2017-04-08
forum: General Help
---

### Post by nuaimat on 2017-04-08
Hello All

I have a Kodi (17.1) media center ubuntu (16.04.2 LTS) setup
my machine goes to sleep every 10 minutes. It's annoying since it even happens when I am watching a movie. even trying to send commands to Kodi using the Android remote (Kore) doesn't bring it back from sleep. the only way to bring it back from sleep is to press a key on the keyboard.

I tried to 
```
tail -f /var/log/*
```

to try and figure out what's causing that sleep, but nothing is being printed out when sleep happens. 
Can you please help me figuring out what's causing that sleep?

PS: I have NVIDIA Corporation ION LE graphics card, with NVIDIA legacy binary driver - version 304.135 (304.135-0ubuntu0.16.04.1) 

Thanks

---

### Post by KenUBF on 2017-04-09
Hi nuaimat,

I've never used the media center version of Ubuntu but just throwing something out there. By any chance have you checked the power management settings of your operating systems? I imagine the sleep settings would be under Power Management. There, should be settings that says, "Put computer to sleep when inactive for:" and "Put display to sleep when inactive for:"  and you have several options, including "Never." Take a look at those settings and see what you find.

---

### Post by nuaimat on 2017-04-11
Hey @KenUBF
thanks for taking the time to reply, I have already checked those options under xscreensaver options ( X directly opens kodi but i can switch to to lightdm ) they are not checked and the whole screensaver is disabled.

any other thoughts?

---

### Post by rogervn on 2017-04-11
Have you tried Caffeine?

[http://ubuntuhandbook.org/index.php/2015/01/install-caffeine-indicator-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2015/01/install-caffeine-indicator-ubuntu-14-04/)

---

### Post by nuaimat on 2017-04-14
> **rogervn said:**
> Have you tried Caffeine?

[http://ubuntuhandbook.org/index.php/2015/01/install-caffeine-indicator-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2015/01/install-caffeine-indicator-ubuntu-14-04/)

I don't have a desktop manager to run caffeine. my system logs in directly to Kodi. 
I am trying [these]("https://unix.stackexchange.com/questions/98921/display-shuts-down-while-watching-a-movie-after-10-minutes-no-matter-the-setting") suggestions, will let you know how that goes.

---

