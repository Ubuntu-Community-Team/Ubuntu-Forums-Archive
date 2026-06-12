---
title: "Keyboard stops working in Ubuntu 14.10 Nautilus"
date: 2014-10-25
forum: General Help
---

### Post by VH-BIL on 2014-10-25
My keyboard stops working in Nautilus. I can reproduce this by the following actions.

I have files Named like "TV Show Name S01E01.mp4" and I press F2 to rename and press ctrl+c to copy. I drag the new file in that I want named "TV Show Name S01E02.mp4" so I press F2 to rename and press ctrl+v to copy so I just have to change the 1 to a 2. After the past action nautilus does not respond to keyboard keys but it does to keys used for navigation such as arrows, enter and backspace.

Is anyone having this issue or know of a way to resolve it?

---

### Post by VH-BIL on 2014-10-25
Update: (But does not resolve the issue)
Nautilus will start to work again when I kill and restart it.

---

### Post by ridgerunner72 on 2014-10-30
Me too. I've not reported it yet because I haven't been able to find a repro set of steps. Yours it pretty consistent but not completely. If I'm presistent enough with your steps it eventually disregards most keyboard input just as you say.

---

### Post by Franklin_Stone on 2014-10-31
I am able to rename any file when Nautilus starts then it will accept no keyboard inputs after that. At least I know I'm not the only one having this problem

---

### Post by Shevchuk on 2014-11-13
Issue on Launchpad: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1385292](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1385292)

---

### Post by PaulusT on 2014-12-11
I may have found a workaround. Try doing: $ pkill ibus-daemon

I found this here:
[https://code.google.com/p/chromium/issues/detail?id=360388](https://code.google.com/p/chromium/issues/detail?id=360388)
It may be the case that the bug only occurs when you have two keyboard layouts, or a language other than US english selected, or something like that.

---

### Post by Mutos on 2014-12-20
Hi all,


This is linked to the ibus "intelligent keyboard entry bus" used for complex entry. You can disable it permanently so it doesn't start at all, so you don't have to pkill it every time.

Go to the "System Parameters" application. Click the Languages button, then on the bottom of the window, you'll have something like "keyboard input system" with "IBus" selected. Select "None" and that's it!

Sorry if I don't know precisely how are the menus and icon named in English, as I got them in French on my machine.

I found this on the internet, but I closed the page, tried some things for other issues and finally rebooted, so I haven't got the link just there. Next time I'll be more precise.

---

### Post by czellweger on 2015-01-29
This indeed **solves the problem**, thank you !

AND it solves keyboard problems in other apps which tended to ignore keystrokes every now and then. Very annoying, indeed. 
Specially **wxmaxima**  (GUI for maxima Computer CAS system) had that problem. 

Steven Hawking and Bill Gates recently warned that artificial intelligence will kill humanity.
So better de-activate "intelligentkeyoard entry bus", it does not seem to do any good to us.;)

Thanks
Chris

> **Mutos said:**
> Hi all,


This is linked to the ibus "intelligent keyboard entry bus" used for complex entry. You can disable it permanently so it doesn't start at all, so you don't have to pkill it every time.

Go to the "System Parameters" application. Click the Languages button, then on the bottom of the window, you'll have something like "keyboard input system" with "IBus" selected. Select "None" and that's it!

Sorry if I don't know precisely how are the menus and icon named in English, as I got them in French on my machine.

I found this on the internet, but I closed the page, tried some things for other issues and finally rebooted, so I haven't got the link just there. Next time I'll be more precise.

---

### Post by TheFacebookAteMyMommy on 2015-03-04
Thanks, this led me to fixing my own problem with Nautilus not recognizing (most) keyboard input. As soon as I killed the `ibus-daemon` process, I was able to type properly in Nautilus. Worth noting that I wasn't able to locate a "System Parameters" application - instead I found the Keyboard/IBus setting under Settings>Language Support.

---

### Post by seanos on 2015-03-27
I most often have this problem with Ctrl+L. I’m reluctant to just remove a feature that I will use from time to time to fix this so I haven’t done anything to iBus.

I have noticed that opening a new Nautilus window will fix this for me, so I thought I’d just check what I had open. I had a main Nautilus window with several tabs and two other single view windows. The main window was the one with the problem and the one I really didn’t want to close since it had so many related tabs open. After swapping back & forth I noticed that although Ctrl+L didn’t *seem* to work in the main window **it was actually triggering** in one of the other windows! After closing the extra windows, the main instance responded fine to Ctrl+L.

I’ve done a couple of tests and Ctrl+L only seems to be affecting the most recently opened Nautilus window when the first window has focus. It works as expected in any newer window. I wonder if this is connected with opening the first Nautilus window through Startup Applications?

---

### Post by alex-garel on 2015-05-13
Thanks disabling ibus, also solved another problem for me : when I am in a file list I use typing to go to a specific file. With ibus, nautilus was not getting the first letter which is annoying ! Without ibus, it works.
That said I hope they will be able to solve ibus problems.

---

