---
title: "Mac/Windows better than Ubuntu during crashes???"
date: 2006-11-01
forum: General Help
---

### Post by Ninjagecko on 2006-11-01
I'm extremely disappointed with how Ubuntu handles freezes. On the Mac, when an application freezes, all you have to do is option-click on the dock and force-quit it, and it will be kill -9'ed. On Ubuntu, when my computer freezes (very often when using Amarok), you lose the ability to move the mouse and use the keyboard (never happens on the Mac except for rare device driver bugs), making it impossible to get out of the freeze without a hard reboot.

And I can't ctrl-alt-f# because the nVidia drivers prevent that -- some ridiculous bug. (And even if they did, your X server should never lock up. What SHOULD happen like on the Mac: The application's window will stop responding, but you should still be able to click on the dock or alt-tab for goodness sake!)

No self-respecting modern computer system should EVER suffer from this "you have no more mouse and keyboard; you have to do a hard reboot; sorry" problem. It is absolutely ridiculous to have an OS that does not have any sort of reliability or fault-tolerance when you need it the most. Single programs should not be able to take down the entire system or even just the GUI.

I'm getting a new computer, but am seriously considering switching away from Ubuntu because of this. I ask you: please give me the info I need to fix this. Will switching X-servers help? Anything here...

(I don't meant to flame, but nomatter how many times I've posted on these forums for help regarding this issue, no one's said a thing, so...)

related: [http://ubuntuforums.org/showthread.php?p=1649950](http://ubuntuforums.org/showthread.php?p=1649950)

tags: crash, freeze, lockup, lock-up, hard crash, hard freeze, UI freeze, GUI freeze, GUI design flaw, design flaw, hard reboot, reboot, X-server, X, Xorg, nVidia, Mac, Apple, OS X, GUI, reliability, fault-tolerance, instability, stability, unstable, common sense, user interface guidelines, UI guidelines, Amarok, stupid, stupidity, bug, severe bug, major bug, unusable, bad programming, bad design, ctrl-alt-f1, ctrl-alt-esc, quit, desktop, force-quit, frozen cursor, frozen keyboard, locked keyboard, OS choice, OS switch

---

### Post by Ninjagecko on 2006-11-04
*bump*

Any suggestions please?
Thank you.

---

### Post by LMP900 on 2006-11-04
You mean, just one application freezing? Assuming that you're using GNOME and you still have control of your mouse:

Right-click the panel

Choose **Add to panel...**

Add **Force Quit** to your panel

---

### Post by LenzM on 2006-11-04
I am having a very similar problem
[http://ubuntuforums.org/showthread.php?t=290898](http://ubuntuforums.org/showthread.php?t=290898)

---

### Post by Ninjagecko on 2006-11-06
Thank you for replying, but I explicitly said the entire mouse/keyboard/everything froze.

---

### Post by hikaricore on 2006-11-06
I've had this issue with a few different applications, the problem ended up being my video drivers, odd as it sounds.  I would get random crashes and lockups from apps I couldn't believe would ever cause this issue (such as flash in firefox).  It may even be your audio hardware, do you notice crashes at other times?  Or is it just from this specific audio application?  You might try using a different application to play music to see if you have a similar crash.  I don't have much more advise to offer than that.  Hope it is of some help to you tho.

---

### Post by doclivingston on 2006-11-06
> **Ninjagecko said:**
> Thank you for replying, but I explicitly said the entire mouse/keyboard/everything froze.

Above you mentioned that you were using the nvidia drivers, and this is probably the cause. I've seen this a number of times, and the issue is some bug in the proprietry nvidia drivers which locks up the X process. The only solutions I've seen are a) if you're lucky, typing Control-Alt-Backspace and restarting X, b) restarting the machine, or c) logging in from somewhere else via ssh and killing X.

---

### Post by hikaricore on 2006-11-06
> **doclivingston said:**
> Above you mentioned that you were using the nvidia drivers, and this is probably the cause. I've seen this a number of times, and the issue is some bug in the proprietry nvidia drivers which locks up the X process. The only solutions I've seen are a) if you're lucky, typing Control-Alt-Backspace and restarting X, b) restarting the machine, or c) logging in from somewhere else via ssh and killing X.

You wouldn't believe the number of times I've had to kick my girl off her comp to login to my system via ssh and pull a "sudo killall gdm"  ROFL.  Had this problem with the i810 drivers until I upgraded to edgy, no more problems after that thanks to an updated set of drivers and new Xserver :)

Not saying this will solve the nvidia driver prolems but just saying it's funny like that sometimes.

---

### Post by Ninjagecko on 2006-11-06
Thank you both for your insight.


Yes, it might be the nVidia drivers; I've had problems with them in the past freezing the X-server from a sleep/standby or anything OpenGL. They also prevent me from using ctrl-alt-f# to get to a text shell (the screen is blank, though I can log in and type commands blind, and they'll work... it's very odd).

I wonder if the ATI drivers have such a problem... I'd definitely switch to ATI if they didn't cause such horrible problems on Linux.


As for seeing about using another app besides Amarok, I guess I'll see if the latest version still has such problems, and complain to the mailing list if it still happens (maybe it's a xine engine problem - i.e. sound drivers as you suggested... maybe...).


The SSH idea sounds like an interesting way to avoid having to restart my computer, but one shouldn't ever have to do that I'd hope. o_O

---

