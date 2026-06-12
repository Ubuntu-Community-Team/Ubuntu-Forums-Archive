---
title: "Choppy Flash video in Firefox, Chrome and Opera"
date: 2015-07-16
forum: General Help
---

### Post by fall2 on 2015-07-16
I'm not sue exactly why but choppy flash video in all my browsers has recently got pretty bad. I use FF/Chrome/Opera.


I use to use shockwave flash version 11 in FF and Opera but now it says:

FF: shockwave 11.2.202.481 and 13.1.2.3(pepper)
Opera: shockwave 18
Chrome: shockwave 18

I just DL chrome yesterday. Also I DL through a term pepperflash & updated but there was a error (showed a Microsoft bios page) when I did it at the end so I left it. 

I'm not sure whats going on here any fixes or should I just reinstall my OS? If so I want the light weight version of Lubuntu and could use some guidance on anything I need to know for the core version installation/setup.

---

### Post by fall2 on 2015-07-16
Ok, so I think something is wrong with flash because HTML5 in Chrome plays better than Flash does. I'm losing 50% of media packets, THATS CRAZY.

I also tryed to uninstall adobe flash through the software center and it just hung up and did nothing.

I think I either need to remove all versions on flash or I need to reinstall a new OS.


I'm at my ropes end media is not watchable in low definition. I have Lubuntu 14.04

---

### Post by mastablasta on 2015-07-17
1. Adobe flash plugin is not being updated anymore by Adobe. only security patches. pepper flash is different as it is part of Chrome.
2. What are your system specs? if the GPU is not supported well (hardware acceleration) and there is a weak CPU then no matter what you try will not work well enough for you.
3. what exactly is the problem you are facing?: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by fall2 on 2015-07-17
For some reason Flash videos have gotten around 5x more choppy than it normally is on all of my web browsers. I'm losing 5x more packets in flash videos.

Specs:
2.20 GHz P-celeron
2 GB ram - 372 MB being used in dashboard with no programs running.
integrated graphics
1024x768 monitor


I installed Lubuntu 8 months ago and it worked well for streaming but just recently streaming got worse. Everything else works, searches the web quick, loads fast. I just don't have a clue why it got so much worse so fast.

---

### Post by fall2 on 2015-07-19
I notice in both FireFox and Opera browsers I am getting crash errors that say:
FF or Opera has unexpectedly crashed.

Weird thing is the browsers are still running and I can use them, I restart them anyway.

does not do this in Chrome.


Any suggestions?

---

### Post by fall2 on 2015-07-19
The problem is flash is not working right and FF + opera browsers keep crashing. I could have a virus or something is setup/installed wrong.

---

### Post by fall2 on 2015-07-20
So what should I do?

---

### Post by PaulW2U on 2015-07-20
Hi fall2, I've renamed the thread title of the first post. Hopefully the change will attract the help of others that were confused by your choice of title.

See [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475) - always best to make your thread title meaningful and concise.

---

### Post by Geoffrey_Arndt on 2015-07-20
No virus.

Just a messed up flash install.

Use the synaptic package manager to completely uninstall (purge) Flash.   Check it is also disabled in FF plugins.

Use synaptic again to re-install flashplugin.

Reboot and then do a system update via the Software Update tool to get latest Flash with patches applied (if/as needed).


Re Opera, unless it is a very old version of that Browser, it should be using pepperflash also as Opera is now based on Chromium.   If you use Opera a lot, you should see if it's the latest version.

---

### Post by fall2 on 2015-07-20
Thanks Geoffrey but I still have the same problem. Choppy Flash and crash errors.

Funny thing is HTML5 in youtube runs perfect with no frames dropped then I run flash and I drop 500 frames in 30 seconds in 360p.

I used to be able to play any and all videos in flash 360p with zero frames dropped and in 480p with very few dropped.


When I uninstalled flash it only uninstalled version 11.2, this was in FF.
Opera and chrome still had flash 18.

Uninstalled and Reinstalled version 11.2, rebooted then updated and reboot again. still the same.

[CENTER][COLOR=#000000]:cry:[/COLOR][/CENTER]

---

### Post by monkeybrain20122 on 2015-07-21
Where did you get pepper flash 13 from??!!

> Also I DL through a term pepperflash & updated but there was a error  (showed a Microsoft bios page) when I did it at the end so I left it

I don't understand this sentence. How many versions of flash do you have and how did you get them?

---

### Post by fall2 on 2015-07-21
I think I it might of been pipelight I DL'ed but I removed that. I not sure really.

I have Flash 11.2 and 13.1 for FireFox plugins, but I just played a youtube video on FF and when I right clicked the video it said: "Learn more about adobe flash player 18.0."

So I guess I am using flash 18 in FF even though I don't have a plugin for it?????
Also in FF and Opera when I expand a video to full screen my lubuntu menu bar stays on top of the video until I click on the video.

In Chrome and Opera I have flash 18.

I used to have flash 11.2 in Opera(I thought), but after I installed Chrome the plugin says flash 18 for Opera. Like it upgraded.

Chrome I just got and it came with 18 already.

Its so weird.

---

### Post by fall2 on 2015-07-21
Originally a while back, I remember going to the adobe flash download page and downloading version 11.2 off their site for FF and DL Opera after that which also used 11.2.

Everything worked well at that time.

---

### Post by fall2 on 2015-07-21
FF plugins in add-ons manager

shockwave flash 13.1.2.3.

last updated 07/06/2015

file libfreshwrapper-pepperflash.so

mimi types application/x-shockwave-flash (shockwave flash: swf),
                 application/futuresplash (futuresplash player: spl


shockwaveflash 11.2.202.491

shockwave flash 11.2 r202

last updated 07/21/2015

file libflashplayer.so
mimi types application/x-shockwave-flash (shockwave flash: swf),
                 application/futuresplash (futuresplash player: spl)

---

### Post by fall2 on 2015-07-21
Come to think of it, I can not remember ever downloading a flash 13. Maybe in some update, I can't recall.

---

### Post by Geoffrey_Arndt on 2015-07-21
Re flash for Firefox . . Adobe froze the versions update for Ff (11.2.xxx is latest).   Only security updates for past couple years.   Chromium based browsers (Chrome, Opera, and others) can get the latest flash.

If you prefer Firefox, another alternative to try is installing mpv player, mpv plugin and youtube-dl.   The plugin is available via Firefox's extension/plugin tool, and the others are available via the USC (ubuntu software center).   On my laptop, mpv works extremely well on certain websites including youtube, but not at all on other websites (espeically social media sites such as Facebook, etc.).     I like that mpv plays youtube videos without the ads . . . note  - - all 3 have to be installed, and the plugin provides an icon in the upper right area of the Firefox panel (or whatever it's called).   You just click on that after you've loaded the page with the youtube video.  The control panel is mouse-over activated (lower middle part of screen).

---

