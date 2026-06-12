---
title: "how do you autoload a program?"
date: 2008-02-06
forum: General Help
---

### Post by freakz on 2008-02-06
Hey, i am a completely new to linux, i have been using windows most of the time due to college and stuff, but now i want to make a switch to linux and decided on uBuntu! but my problem is how do i make a program autoload on login like under windows.

i just want uTorrent (under WINE) to autoload on login!

thanx

freakz

---

### Post by Steveway on 2008-02-06
> **freakz said:**
> Hey, i am a completely new to linux, i have been using windows most of the time due to college and stuff, but now i want to make a switch to linux and decided on uBuntu! but my problem is how do i make a program autoload on login like under windows.

i just want uTorrent (under WINE) to autoload on login!

thanx

freakz

Look at the session-settings.
But the real question is: Why are you using uTorrent, a windows-application, if there are equal and even better linux-native programs for the same task?
You should use Deluge-torrent or if you use KDE Ktorrent.

---

### Post by SOULRiDER on 2008-02-06
I suggest you get rTorrent, its the lightest one. Even if its CLI its still very easy to use/configure. I will write a guide on how to configure it soon.

---

### Post by PinkFloyd102489 on 2008-02-06
Ktorrent is probably the most like uTorrent. Stay away from Azureus, as it eats too many system resources in my experience.


> **SOULRiDER said:**
> I suggest you get rTorrent, its the lightest one. Even if its CLI its still very easy to use/configure. I will write a guide on how to configure it soon.


It's generally not a good idea to steer a new Linux user to the command line.

---

### Post by drs305 on 2008-02-06
To answer your original question, System, Preferences, Sessions, Add. You then name it and enter the command to start the program. It will then start each time ubuntu starts up. The command would be something like:
wine "c:\program files\programfolder\program-name.exe"

---

### Post by bodhi.zazen on 2008-02-06
> **SOULRiDER said:**
> I suggest you get rTorrent, its the lightest one. Even if its CLI its still very easy to use/configure. I will write a guide on how to configure it soon.

+1 rtorrent

Here is a guide : [http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/](http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/)

Personally I launch rtorrent with screen

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)

[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

---

### Post by freakz on 2008-02-06
a. Thank you for all of your quick replies...

The reason i am using uTorrent for the moment, is because i have transfered from windows, but i still need to be familiar with a few things, like my torrent client. After i am happy with uBuntu and the way things are going i will install a native linux client. For the moment though, i am sticking with uTorrent...

Thank you for all of your feedback, When i try a new client i will try rTorrent with a screen!!! :)

freakz

---

### Post by nilarimogard on 2008-02-06
There is a problem with deluge, ktorrent, rtorrent and any other bittorrent client that also make me use utorrent (the only windows piece of software i use in ubuntu): they can't handle 100+ torrent well, or at least on my system. I'm seeding more than 100 torrents and they all stop responding or just eat all my resources, while utorrent... well, it's like i don't even know it's running.

---

