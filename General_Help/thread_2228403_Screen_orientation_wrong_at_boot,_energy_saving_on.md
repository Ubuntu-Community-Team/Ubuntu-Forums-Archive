---
title: "Screen orientation wrong at boot, energy saving on even it's turned off"
date: 2014-06-07
forum: General Help
---

### Post by lauri.t.kumpulaine on 2014-06-07
I have this Intel Nuc computer.

[http://www.intel.com/content/www/us/en/nuc/nuc-board-dn2820fykh.html?wapkw=dn2820fykh](http://www.intel.com/content/www/us/en/nuc/nuc-board-dn2820fykh.html?wapkw=dn2820fykh)

I installed Xubuntu 14.04 on it and all hardware is working perfectly, including bluetooth and wireless. However there is some problems with Xubuntu.

1) I set screen orientation to 'portrait', because I use large screen in portrait mode for reading ebooks and other pdf documents. It works, from settings, but the log in screen is still in 'landscape' mode.

2) I have set the energy saving settings to 'never', but still my pc goes into hibernation and for example the music that I am playing stops. How I can set those energy saving options so I can have my screen going into energy saving mode and I can still listen the  music? I usually keep some music on from the PC even that I am not using it.

3) Language problem with Finnish and English. I have set my language as Finnish, but there still are some words in English, like desktop shortcuts to filesystem etc.

Xubuntu 14.04 feels rock solid! :-]

---

### Post by Toz on 2014-06-07
> **lauri.t.kumpulaine said:**
> 1) I set screen orientation to 'portrait', because I use large screen in portrait mode for reading ebooks and other pdf documents. It works, from settings, but the log in screen is still in 'landscape' mode.
Have a look at [this thread]("http://askubuntu.com/questions/408302/rotated-monitor-login-screen-needs-rotation") for what looks like a solution.

> 2) I have set the energy saving settings to 'never', but still my pc goes into hibernation and for example the music that I am playing stops. How I can set those energy saving options so I can have my screen going into energy saving mode and I can still listen the  music? I usually keep some music on from the PC even that I am not using it.
Have a look through the Power Manager applet in Settings Manager to make sure that you don't have it set to suspend or hibernate after some time of inactivity. And if you're using xscreensaver as your screensaver instead of the default light-locker, look through the xscreensaver preferences (advanced tab) in settings manager as well.

> 3) Language problem with Finnish and English. I have set my language as Finnish, but there still are some words in English, like desktop shortcuts to filesystem etc.
The Xfce team is currently putting in considerable effort towards translation. If you've found something that is missing please either create a bug report over at [https://bugzilla.xfce.org/]("https://bugzilla.xfce.org/") (in your case against the xfdesktop application) or try to get a hold of someone at the [#xfce IRC channel]("irc://irc.freenode.net/#xfce").

> Xubuntu 14.04 feels rock solid! :-]
+1

---

### Post by lauri.t.kumpulaine on 2014-06-09
Thanks for your response Toz. I did not remember the screen orientation correctly. It did not work in 13.10 eather, it worked on W8. And after all, it's not that big of a deal since you usually just type your password and log in. I could make the script, but I use the screen portrait and landscape, so actually I would have to switch it manually everytime.

Problem with the screen locking was the light-locker, and that is solved now.

---

