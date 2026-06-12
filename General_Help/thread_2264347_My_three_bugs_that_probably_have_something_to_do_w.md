---
title: "My three bugs that probably have something to do with GNOME 3...."
date: 2015-02-06
forum: General Help
---

### Post by Yusuf_Ibrahim_Rama on 2015-02-06
So... I was using Ubuntu 14.10 with my Acer Aspire E 14 laptop and I encountered these three bugs:

1. Ubuntu *sometimes* couldn't boot. This is *not* to be confused with the other booting problem(s) where Ubuntu cannot boot at all. Mine was unpredictable: sometimes it booted, but about half to four-fifth of the time my laptop would only display a black screen with a typing-cursor blinking. This happened after GRUB, after you select which OS to boot. When this happened, my only option was to force-power off the laptop and start it all over again, hoping for the half to one-fifth chance that Ubuntu would boot normally.

I do know that some other people have encountered this problem of mine and I saw their posts asking for help, but I found that they got none. The thing is, I guess, this problem was almost always confused with the other booting problem(s) that had something to do with graphics card. Mine, I think, had something to do with GNOME.

2. Ubuntu couldn't power off the laptop. When I shutdown my laptop, Ubuntu would only halt all the processes, but it couldn't power off the laptop so I had to force power off it manually. It was safe, though, since no more proecesses were going, but this still posed a problem: it could neither restart nor hibernate properly.

3. I couldn't right-click with my touchpad, so I had to always use a mouse. It's not the hardware--I tried testing my touchpad settings and when I clicked the button that was supposed to make a right-click, it was read as a left click. I also tried to check the left-handed option where the buttons were inverted and so a right-click would be the primary click, but still I couldn't make a secondary click by clicking the left button of my touchpad. In short, both the left and right buttons of my touchpad were read as primary buttons.

Yesterday I switched to Debian GNOME. The three bugs were gone, but GNOME 3 couldn't load either so the desktop was replaced by something that I guess was GNOME Classic. (I am quite sure that if GNOME 3 could load on my Debian, the three bugs would have manifested themselves again.) Then I switched to Debian KDE. Everything was fine, but I didn't know how to set up my internet on Debian (and lack of internet connection was crippling) so I instantly switched to Fedora, with which I am writing this post right now.

Yet, Fedora uses GNOME 3, and I find the bugs manifesting again, except bug number 1 (or perhaps it just hasn't begin occuring yet, since it occurs by the half to four-fifth chance).

I love Ubuntu more than I do Fedora, but I think I'm not going to switch back until I can certainly fix these problems (especially number 1) or until the bugs are fixed in a future release. So, I wonder if you have some solutions to these problems?

Oh, yea. Last thing, I'm a novice. I had used Ubuntu for some months, but I don't understand more complicated computing terms, so... please answer with simple words, would you?

Thanks!

---

### Post by Bucky Ball on 2015-02-06
We can't really help you troubleshoot your issues with Ubuntu if you don't have it installed. If you have a spare partition, install 14.04 LTS and let us know if you are still having the same issues. 14.04 LTS is more stable than 14.10 and is supported for five years (April 2019). 14.10 for another six months, but it may have more current hardware drivers if that is your issue. Try 14.04 first, perhaps, and switch if you have very new hardware. 

Debian and Fedora are not supported in the main support areas here. They have sub-forums [here]("http://ubuntuforums.org/forumdisplay.php?f=446"), but:

> Please be aware this is not the best place to receive tech support for these OSs/Distros and users should look for official support channels for those systems.

Good luck. ;)

---

### Post by Yusuf_Ibrahim_Rama on 2015-02-06
> **Bucky Ball said:**
> If you have a spare partition, install 14.04  LTS and let us know if you are still having the same issues.

Well, I happen to have used 14.04 before the 14.10 was released. Bug no. 3 (right-click issue) didn't happen on 14.04, but bug no. 2 (shutdown issue) did. About bug no. 1, though, I can't tell because I was having another boot issue that happened because I erroneously checked the LVM thing when I was installing it.

---

### Post by Bucky Ball on 2015-02-06
Well, sounds like 14.04 LTS got rid of bug #1 and possibly #3. We can certainly help you troubleshoot #2, but as I say, you'd need a running install for us to do that. Avoid setting LVM this time. ;)

PS: Instead of hard shutdown, which isn't great for your hardware, when stuck at a black screen when you try to shutdown (if that happens on a reinstall of 14.04), can you hit control+alt+F1 and get to a login cursor? If so, login and:

```
sudo reboot -h now
```

---

