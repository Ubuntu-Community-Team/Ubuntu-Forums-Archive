---
title: "Firefox doesnt display Youtube and Facebook"
date: 2014-12-01
forum: General Help
---

### Post by darko6 on 2014-12-01
Since i have installed 14.04 firefox seems to not support Youtube and Facebook. I have tried everything. Is there any alternative way to make it work?
I have below uploaded pictures of youtube page and  firefox plugins and extensions. Thanks!

---

### Post by carlwsnyder on 2014-12-01
In your Firefox plugins, you have listed Shockwave Flash 15.0.0.223, as well as the Linux version 11.2.202.424.  I have no way to confirm that there is even a version of Shockwave Flash 15.0.0.223, and definitely this plug-in is not available from the Ubuntu repository system.  That at least must be removed.

Not all of YouTube or Facebook will work with Firefox on Linux, even with the latest software available.  You can download and install Chromium with pepperflashplugin-nonfree or Google Chrome with its built-in pepperflash plug-in to play the latest Facebook flash games or view all of the DRM protected flash video on YouTube, but these will not work under Firefox on Linux.  For more information, see article [http://www.howtogeek.com/193876/using-firefox-on-linux-your-flash-player-is-old-and-outdated/](http://www.howtogeek.com/193876/using-firefox-on-linux-your-flash-player-is-old-and-outdated/)

---

### Post by darko6 on 2014-12-01
Thank you. [COLOR=#000000]Shockwave Flash 15.0.0.223  is [/COLOR]a pepperflash. Do i have to remove both Shockwaves  or just that one? And how to do that? I have Chromium with pepperflash but it keeps crashing. Its annoying. I have Chrome and its OK but i have used to Firefox. Is there any alternative flash players?

---

### Post by the-tech-kid on 2014-12-02
Here is what you should do:
Open the ubuntu software centre and hover over the menu bar at the top.
Click edit, and click software sources.
Then click "Other Software".
Now tick "Canonical Partners" and click close (you will need to be a administrator).
Now install adobe-flashplugin like any software.

---

### Post by darko6 on 2014-12-02
Nope, still doesnt work.

---

### Post by papibe on 2014-12-02
Hi darko6.

A few ideas:

Try opening Firefox with no pluggins to see if there's one causing the problem:
```
firefox -safe-mode
```
If that does not help you could reset your profile:
```
firefox -P
```
then delete and create the default profile, and make sure it is selected as the default.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by darko6 on 2014-12-03
Hi papibe,
I tried that but didnt help. All plugins stay where they where even in safe mode. Dont know what to do anymore.

---

### Post by oldos2er on 2014-12-03
Moved to General Help.

---

### Post by afrodeity on 2014-12-15
Am having similar trouble since upgrading to Trusty

[IMG]http://imageshack.com/a/img909/9044/YA3XID.png[/IMG]

adobe-flashplugin is installed.

none of the browsers including firefox and chromium can access facebook properly.

---

### Post by don62 on 2014-12-15
I upgraded to ubuntu 14.04 LTS some time ago.
Had no problems until recently when iPlayers (both BBC & ITV), 4oD, Youtube etc
failed to show video & displayed the following message:-
Failed to load "libpepflashplayer.so"
Have tried various solutions mentioned in this thread, but nothing worked.
Maybe nothing to do with the problem, but I now see that when I press the  " and @ 
on my keyboard,  @ and " displays, ie the display has switched from the keys pressed.

---

### Post by Jesse_Campton on 2014-12-15
Try updating your Shockwave Flash. 16.0.0.235






[ATTACH=CONFIG]258603[/ATTACH]

---

