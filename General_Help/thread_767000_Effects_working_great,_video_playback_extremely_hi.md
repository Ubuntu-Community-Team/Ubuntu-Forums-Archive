---
title: "Effects working great, video playback extremely high CPU usage"
date: 2008-04-25
forum: General Help
---

### Post by wiberg on 2008-04-25
Hi,

I did a fresh install of Hardy Heron yesterday. I have been using Gutsy before with Compiz Fusion and only minor problems.
Now everything works splendid except for video playback. I get close to a 100% CPU usage when I watch a video in full screen. The whole system becomes sluggish and Compiz will lag. There is an extra (loud) fan in my case which will go off every few minutes when video (also flash video) is being played. I played around with media players, mostly VLC (my favorite) and Totem. In VLC I changed the output module to everything that makes sense with no effect. I also turned off Compiz in favor of Metacity, but that too helped little.
My specs:

Intel Pentium 3 GHz Dual Core
1 Gb RAM
ATI Radeon X1300 graphics card
Driver: fglrx (installed via proprietary drivers manager)
Compiz Fusion with Emerald themes
[COLOR="Red"][xorg.conf (http://pastebin.ca/997477)]("http://pastebin.ca/997477")[/COLOR]
the xorg.conf is a little cluttered due to installation problems... I also tried tweaking it a little following [COLOR="Red"][these]("http://ubuntuforums.org/showthread.php?t=756182")[/COLOR] steps with no effect so i took the changes back.
Under Gutsy I had to use XGL, which I tried today with even worse video playback performance.

If anybody has any ideas, it would be greatly appreciated! :)
If you need further information I will be happy to gather everything.
Thanks!
wiberg

---

### Post by tommcd on 2008-04-26
I have been getting very high cpu usage from flash videos in Gutsy and Hardy. I think I had it in Fiesty too, but I can't remember. It happens on my desktop (AMD with nvidia graphics card) and laptop (Intel). I do not use compiz, and I have composite disabled in xorg.conf. I use no Firefox addons.
I solved the flash problem by removing flash-player-nonfree from synaptic (mark for complete removal) and installing the flash plugin from adobe.com. Just untar it and copy libflashplayer.so to /usr/lib/mozilla/plugins. I also had to create symlinks to /usr/lib/firefox-3.0b5/plugins like this:
"sudo ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-3.0b5/plugins/libflashplayer.so". This solved the high cpu usage with flash.
For other videos, do you just mean in firefox streaming video on the web? or videos you download to your home directory? Check that you have direct rendering enabled for you graphics card. Also perhaps try mplayer. I think mplayer is still the best video player for linux.

---

### Post by wiberg on 2008-04-27
I checked on direct rendering, it is activated. I didn't try installing flash from adobe.com yet, maybe I will do so later. Mainly I have issues playing video files on my hard drive, like ripped movies or so. Both cores go up to 100% usage. I didn't have any problems with neither flash nor video files on gutsy nor feisty. So it has to be some issue with hardy... I don't think the problem is due to Totem or VLC as they played nicely with gutsy and feisty. VLC fits my needs better than mplayer too, so I don't think I will switch to it :)
Thanks, I am still open for more suggestions :D
wiberg

---

### Post by solarwind on 2008-09-07
I have an ATI mobility x300 card in my laptop. While playing flash videos (ex. youtube) CPU usage goes to 30% - 50% and higher when full screen. Haven't tested playing videos on hard drive yet.

What's your CPU usage while playing flash videos (to those without issues)?

I am using "top -d 1" to view CPU usage while playing videos as the system monitor takes up a lot of cpu time on its own while graphing statistics.

---

### Post by solarwind on 2008-09-07
Here's a screenshot:

[[IMG]http://img366.imageshack.us/img366/5867/screenshot1mo7.th.png[/IMG]](http://img366.imageshack.us/my.php?image=screenshot1mo7.png)

Between 30 and 50 seconds was watching a youtube video full screen. Is this normal? The CPU usage is wayyyyy too high.

---

