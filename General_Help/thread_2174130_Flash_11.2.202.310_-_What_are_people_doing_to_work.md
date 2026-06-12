---
title: "Flash 11.2.202.310 - What are people doing to work around flash?"
date: 2013-09-13
forum: General Help
---

### Post by Richard85 on 2013-09-13
I did the most recent flash update and now my browsers are working horribly! I can't watch youtube videos. I can't properly manage my tumblr. I can't properly use online homework software for the math courses I teach.
I get the same results whether I'm using Firefox, Chrome, or Chromium. Lagging and crashing.
When I look around at the forums, the only replies I see are along the lines of "yeah, it sucks. deal with it." or "use Chrome" (which doesn't seem to be working). 
My specs for my system76 laptop 12.10 64-bit, Kernel 3.5.0-40-generic, GNOME 3.6.0.
Any thoughts? references? links? workarounds?

---

### Post by kostkon on 2013-09-13
Actually, Chrome has its own built-in Flash (usually the latest version of it, and thus not 11.2.x), so the cause of your problems might be something else that is unrelated to that particular security update for Flash.

I got the same update and my Flash is still working fine.

---

### Post by Mephisto Pheles on 2013-09-13
I too doubt that this is related to the flash update only. Something else must have happened there.

---

### Post by Z1-900 on 2013-09-13
I specifically installed 32-bit Ubuntu 13.04 so that I could use Google Chrome with its pepper based flash player. The outdated except for security updates flash player that Firefox or Chromium uses never seemed to work that well for me so I uninstalled it and just use Google Chrome for sites that need flash, gaming,Youtube,etc.. I would have loved to have stuck with x64 Ubuntu but I thought I read Google Chrome's pepper based flash player did not work in an x64 operating system I can't remember the details for sure though.

---

### Post by Mephisto Pheles on 2013-09-13
Chrome works fine on 64 bit machines. You must have misread something there. You need SSE2 support from your processor for latest flash though. Most 64 bit processors should have SSE2.

---

### Post by tgalati4 on 2013-09-14
Without sse2 support, your CPU has to emulate it in software which might slow things down.

tgalati4@Mint14-Extensa ~ $ cat /proc/cpuinfo | grep sse2
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse **sse2** ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse **sse2** ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm d

---

### Post by kostkon on 2013-09-14
> **tgalati4 said:**
> Without sse2 support, your CPU has to emulate it in software which might slow things down.
Actually on non-sse2 systems flash simply segfaults.

---

### Post by johnlittler on 2013-09-25
I am replying to your general question of "What are people doing about flash"
.
Year by year the number of websites using flash is declining. It is the Adobe company who will have to live without flash and not you.

This answer will be of interest to you if you like using the terminal. If you are not used to the terminal, it is probably something you may not be interested in.

If you are using Firefox 24 or above, you can make a few changes to your Linux system and Firefox to enable you to watch in html5 ( H-264, mp3-aac ) without any plugin all the videos on Youtube ( which have been uploaded within the last two years) without entering the html5 trial and other sites like dailymotion.com.
see:
[http://www.ghacks.net/2013/06/23/firefox-24-for-linux-gets-native-mp3-aac-and-h-264-support/](http://www.ghacks.net/2013/06/23/firefox-24-for-linux-gets-native-mp3-aac-and-h-264-support/)


If you are interested, these are the steps to follow:

1. Type about:config into the firefox browser's address bar and hit enter.
2. Confirm that you will be careful if this is your first time.
3. Search for media.gstreamer.enabled
4. Make sure it is set to to true (which means enabled).
5. You need to install gstreamer: `libgstreamer0.10-dev` and `libgstreamer-plugins-base0.10-dev`

In the Ubuntu terminal ( open with ctrl + alt + t ) type these lines separately. Press enter after each line of code.

$ sudo apt-get install libgstreamer0.10-dev

$ sudo apt-get install bgstreamer-plugins-base0.10-dev

sudo add-apt-repository ppa:gstreamer-developers/ppa
sudo apt-get update
sudo apt-get install gstreamer1.0*

6. Install the following Firefox extension (to view Youtube videos)

[https://addons.mozilla.org/ja/firefox/addon/youtube-all-html5/?src=api](https://addons.mozilla.org/ja/firefox/addon/youtube-all-html5/?src=api)


7. Deactivate the flash plugin. There is no need to remove it. Just deactivate it. ''Add-ons &#8594;Plugins&#8594;ShockwaveFlash&#8594;Never activate

8. Restart Firefox. It is unlikely that you will need to restart your computer, but if these steps do not work restart.

9. Now test it with the flash plugin deactivated.

From Firefox 24, you can view Youtube without flash without joining the HTML5 trial.

Test it on non-Youtube tube videos such as Dailymotion.com and this test video.

[http://mirrorblender.top-ix.org/movies/sintel-1024-surround.mp4](http://mirrorblender.top-ix.org/movies/sintel-1024-surround.mp4)


10. You may need to reactivate flash for other sites. To do that easily, install this Fiorefox extension:

[https://addons.mozilla.org/en-US/firefox/addon/flash-onoff/](https://addons.mozilla.org/en-US/firefox/addon/flash-onoff/)


An icon can be dragged from Menu Bar&#8594;View&#8594; Toobars&#8594;Customize to a toolbar and clicking it can turn flsh on and off.

---

