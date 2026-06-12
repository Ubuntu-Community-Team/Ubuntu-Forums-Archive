---
title: "(SOLVED) Lubuntu no longer fills entire screen..."
date: 2014-06-26
forum: General Help
---

### Post by oCyiIsejN9jk on 2014-06-26
Hi all...    I'm working on an old dell laptop (Latitude C640) with Lubuntu 12.10 installed on it that belongs to a friend of mine. He was watching a movie using Firefox and when he paused it to get something to drink, when he came back, the desktop no longer occupied the whole screen and the toolbar no longer shows. There is now a sizeable gap on both sides of the screen. I've tried tinkering with Lubuntu's  resolution settings to no avail and I would need precise instructions if this is going to involve editing configuration files. Can I get help getting the laptop back to normal?     I've confirmed the correct video driver (the open source radeon driver) is loaded for the Radeon 7500 graphics chipset. If there is any other information you need, please let me know.    Thanks! :KS

---

### Post by oCyiIsejN9jk on 2014-06-27
Anyone? I would rather not have to reinstall the entire OS for what could be a simple fix. Would purging the video driver entirely (and then reinstalling it) do the trick? If so, what is the command for that? I've looked around on the net for solutions but what I've found is either not for this version of Lubuntu or involving a traditional xorg.conf file which this system doesn't have. What's interesting is that the screensaver works fine and uses the entire screen. Thanks...

---

### Post by Mike_Walsh on 2014-06-27
Hi.

Interesting you should mention this problem! I've recently installed Lubuntu 14.04 on an elderly Dell Inspiron (11 years old!), and I've got precisely the same problem. On initial installation, the desktop was squashed up into the top left corner of the screen, with lots of weird squiggly stuff round it. I've used information from this post here:-

[http://ubuntuforums.org/showthread.php?t=2222349](http://ubuntuforums.org/showthread.php?t=2222349), and also this one:-

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

The guy in the first thread is using the exact same make, model AND hardware as mine. However, the solution that worked for him doesn't seem to work for me, so I've taken the the advice of Morgaes in the second thread and used the 'nomodeset' setting, which is supposed to override the native Dell driver, and it sort of works; I now have a 640x480 display sitting in the middle of the screen (which is 1024x768) with a black band all the way round it. Perhaps the advice given here would solve your problem.....I don't know. It's worth a try, and if it works, you wouldn't need to re-install the O/S.

It seems to be a common problem with many of the older Dells; there's several postings on the forums about this very problem. I've tried 3 different distros on the Dell, and they all have the same problem, so I guess it's hardware-related, NOT the O/S.

If you find another workaround, would you let me know, please? Thanks.

Mike.

---

### Post by oCyiIsejN9jk on 2014-06-27
Hi Mike....Thank you for your help! It turns out that the problem was some additional panels that had been created and nothing to do with the video. I was able to fix the problem. Thanks again! :KS

---

### Post by Mike_Walsh on 2014-06-28
Hi again, Aaron. 

Ummm; when you say 'extra panels created', what exactly do you mean? Care to share? Perhaps it's the same problem I've got.....I would REALLY like to get it fixed!!

Mike.

---

### Post by oCyiIsejN9jk on 2014-06-28
Hi Mike....Lubuntu refers to the bottom toolbar as a "panel." My friend had somehow created two (one one each side) and were automatically set at around two inches in width. The clue came to me when I right clicked on this two inch empty space and was given the option to delete the panel. At first, I didn't because I thought that would delete the bottom toolbar. The other clue was that the bottom toolbar took up the entire length of the monitor, not just the desktop area. Also, how are you able to write using spaces? The forum software isn't letting me do that. It always shows up as you see it now. Thanks... :KS

---

### Post by Mike_Walsh on 2014-06-29
Quite simply, I just hit the "Enter" key as many times as I want lines. I hadn't noticed any problems with the forum software, I must admit! 

Just the way I've ALWAYS written... (lol)

Unfortunately, that's not the case with my old girl; the taskbar is squashed into the same space in the middle of the screen as the desktop. The desktop is in miniature, with the exception of the icons.....they're full-size, net result being that a dozen or so icons completely fill the desktop. 

Mystifying.....

Mike.

---

