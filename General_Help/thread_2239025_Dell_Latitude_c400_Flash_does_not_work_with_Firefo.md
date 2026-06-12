---
title: "Dell Latitude c400: Flash does not work with Firefox"
date: 2014-08-11
forum: General Help
---

### Post by Alfredo_Martinez on 2014-08-11
Hi,
I have done a fresh installation of lubuntu 14.04 on dell latitude c400. All works ok but not the flash plugin in firefox v 31. The flash plugin is installed according with the package tool and firefox plugin tab but white page is shown when trying to play a web video. Thanks for the help. Regards.

---

### Post by ajgreeny on 2014-08-11
What cpu does your machine have?

Run command ```
cat /proc/cpuinfo | grep sse
``` to see if there is any mention of sse2 in the "flags" output line.  If sse2 is not shown I'm afraid your machine will be unable to use the latest versions of flash for Linux (11.2.202.394 or any of the 11.2 series).  Regrettably, if that is the case you will not be able to use Chrome with the pepperflash plugin either; the newest version of flash that works will be 11.1.102-63, but that may no longer be available and does have security risks.

---

### Post by Alfredo_Martinez on 2014-08-11
Thanks for your fast reply. I see "sse" cpu flag so this means the latest version of flash will not work. Do not you recommend to install the older version you mention? Is there a browser with a built-in version that works for cpu with this flag? Regards

---

### Post by Dennis N on 2014-08-11
Wow that's interesting. That machine seems to have used a Pentium 3 and those sse2 capabilities only were included with Pentium 4, as indicated here: [http://en.wikipedia.org/wiki/SSE2](http://en.wikipedia.org/wiki/SSE2)

It was also a very expensive machine when new - an old PC Magazine found on Google shows it retailed for $2,995. How far we have come.

You can still get any older flash version from Mozilla's archive, which you could do if you find no other option and accept the possible risks.

---

### Post by nerdtron on 2014-08-11
Hhhmm..... Just passing by...

Have you installed the restricted extras package? And have you installed all updates from the update manager?

---

### Post by Alfredo_Martinez on 2014-08-12
Thanks both for your replies. The cpu is pentium iii and the flag is sse not sse2. I have also installed the restricted extra packages and latest updates but still not working.... For installing an old version I guess only I need to replace the plugin file do not I? Thanks

---

### Post by Dennis N on 2014-08-12
> **Alfredo_Martinez said:**
> Thanks both for your replies. The cpu is pentium iii and the flag is sse not sse2. I have also installed the restricted extra packages and latest updates but still not working.... For installing an old version I guess only I need to replace the plugin file do not I? Thanks

Yes. I assume you found the archive page with Google? Search for 11.1.102.63 which is the version ajgreeny says might work. Download the 174mB archive package which contains archives of all the plugins for all platforms. You need to extract the right one for 32 bit Linux which ends with 'linux.i386.tar.gz'. Then once that archive is extracted, open it and extract again to get the actual plugin which is libflashplayer.so

Type about:plugins in the Firefox address bar to see the path to where the libflashplayer.so plugin is located and replace the one there with the archive version. Restart Firefox and hopefully it should work.

Added: If it works, lock the flashplugin-installer package so the system doesn't replace yours with a future update.

---

### Post by Alfredo_Martinez on 2014-08-12
Dennis thanks. Yes I found the old version. I will follow your guideline and advise about the result. Regards

---

### Post by Alfredo_Martinez on 2014-08-12
Dennis, it worked but the videos when playing are choppy. When displaying technical information of the built-in web video I can see 1.3 fps and 5K lost frames when video ends. I had the same issue when using windows xp. Is there any option to minimize (or mitigate) this issue? Thanks. (my internet connection is wired and the speed is 10Mbps)

---

### Post by Frogs Hair on 2014-08-12
You could try this add-on for YouTube based videos . [https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/](https://addons.mozilla.org/en-US/firefox/addon/youtube-all-html5/)

---

### Post by Dennis N on 2014-08-12
> **Alfredo_Martinez said:**
> Dennis, it worked but the videos when playing are choppy. When displaying technical information of the built-in web video I can see 1.3 fps and 5K lost frames when video ends. I had the same issue when using windows xp. Is there any option to minimize (or mitigate) this issue? Thanks. (my internet connection is wired and the speed is 10Mbps)

Pleased to hear that the older flash plugin is working. Give much credit to ajgreeny who really diagnosed your problem. As to the low quality of video, especially noticeable full screen, I would suspect just the lack of processing power with the P3. I get choppy video also on a P4 processor I have on an old XP machine. I would think HD is probably not feasible. You can try the HTML5 video player - temporarily change the player here on Youtube to see:

[https://www.youtube.com/html5](https://www.youtube.com/html5)

or try the plugin mentioned in a previous post. Still, the majority of videos use flash player, I think. You may have to use the smaller size window for better flash video.

---

### Post by claracc on 2014-08-13
> **Alfredo_Martinez said:**
> Dennis, it worked but the videos when playing are choppy. When displaying technical information of the built-in web video I can see 1.3 fps and 5K lost frames when video ends. I had the same issue when using windows xp. Is there any option to minimize (or mitigate) this issue? Thanks. (my internet connection is wired and the speed is 10Mbps)

You cannot expect more of your machine.

I also have a pentium III laptop which cannot use flash player beyond 11.1.102-63 and certainly the flash videos are playing in slow motion and with 100% CPU usage.

You can try, if you use firefox, to use the viewtube script, which can be installed through greasy monkey addon. It will use another less consumption resources format than flash (mp4) to play the videos, but it only works in some sites, youtube is one.

---

### Post by Alfredo_Martinez on 2014-08-13
Thanks for the replay. The videos in youtube are not choppy but after 10 minutes playing the X11 crashes and all the screen goes black with the sound in background running and I need to restart the laptop. I observed that X11 config does not include the dell c400 video card type so maybe this is the problem. Any idea how to detect the video card driver and configure in the X11 server? Thanks

---

### Post by Dennis N on 2014-08-13
Could possibly be the power saving features in the OS coming on after 10 minutes of any keyboard or mouse inactivity, regardless of any video playing at the time. These are the power manager, DPMS, and screensaver (light-locker is installed in Lubuntu). Although normally these should not crash the computer and force a restart. But on your old system, maybe one of these is suspect.

For DPMS background, look up DPMS: Display Power Management Signaling.

On my Lubuntu 14.04 system, power manager is set to never put monitor to sleep. I also disable light-locker, and install xscreensaver to defeat DPMS (see link below). I can control screen blanking (going to black) from xscreensaver.

See this bug report comment:
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716/comments/15](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1193716/comments/15)

It works because Xscreensaver overrides DPMS.

---

### Post by Alfredo_Martinez on 2014-08-13
Dennis, thanks. I will check and advise. Youtube videos are not choppy but from other TV web ([www.rtve.es](www.rtve.es) which is the primary TV channel at Spain) yes showing low FPS rate and frame discards in the technical stats when video ends... so I am wondering if choppy video output depends also of the front-end web server.... Not really sure what does it mean FPS rate and if there is a way to inprove at network card level (layer 2) in the laptop. Regards,

---

### Post by Alfredo_Martinez on 2014-08-14
Dennis, it worked. Disabling light-locking and installing xscreensaver has fixed the black screen issue.

Using vlc or gnome-mplayer to play local videos the video and sound are not in sync. Just using mplayer2 via command works perfectly but lower screen resoltion: 720x460. I think is a video card driver performance issue because is a generic one (in windows xp worked but having the specific dell driver). But it is working. Now I will test SMplayer to avoid using command line..... Thanks for your support. Regards.

---

### Post by ajgreeny on 2014-08-14
You could always continue to use mplayer from command line and simply hit f for fullscreen

---

### Post by Dennis N on 2014-08-14
> **Alfredo_Martinez said:**
> Dennis, it worked. Disabling light-locking and installing xscreensaver has fixed the black screen issue...Now I will test SMplayer to avoid using command line..... Thanks for your support. Regards.

Aha...I thought there was a good chance that would work. As to videos, SMPlayer is my player of choice. The YouTube browser that works with it plays videos from YouTube without needing flash player.

---

### Post by Alfredo_Martinez on 2014-08-16
The SMPlayer works fine having video and sound in sync but observed that cpu is always 100% and radomly the video is choppy.....I am wondering how can be minimizing cpu high consume....

---

