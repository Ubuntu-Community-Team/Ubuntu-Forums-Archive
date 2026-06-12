---
title: "Getting Firefox to play embedded mp3"
date: 2007-01-06
forum: General Help
---

### Post by ArmchairAthlete on 2007-01-06
That's it, how do I make firefox play embedded mp3s? I need my ytmnd sites to work properly =). 

I thought it would be simple but after a little searching I can't find the right plugin. Maybe I'm blind.

---

### Post by obsidion on 2007-01-06
> **ArmchairAthlete said:**
> That's it, how do I make firefox play embedded mp3s? I need my ytmnd sites to work properly =). 

I thought it would be simple but after a little searching I can't find the right plugin. Maybe I'm blind.

  A little info as to what and how you have installed anything would help us to help you, maybe a link to one of the sites you are talking about so others can test their plugins on them and make sur eit isn't a fault with the site rather than firefox and plugins would help too.

---

### Post by ArmchairAthlete on 2007-01-06
Sure, it's a pretty vanilla install of Ubuntu 6. I installed Flash but not much else for Firefox. Also installed build-essentials, gcc, zsnes, not much else. 

A link:
[http://gandalfsridinspinnaz.ytmnd.com/](http://gandalfsridinspinnaz.ytmnd.com/)

edit: This isn't running off the liveCD either but is an actual install.

---

### Post by obsidion on 2007-01-06
> **ArmchairAthlete said:**
> Sure, it's a pretty vanilla install of Ubuntu 6. I installed Flash but not much else for Firefox. Also installed build-essentials, gcc, zsnes, not much else. 

A link:
[http://gandalfsridinspinnaz.ytmnd.com/](http://gandalfsridinspinnaz.ytmnd.com/)

edit: This isn't running off the liveCD either but is an actual install.

Ok works fine for me, with the mozilla-mplayer plugins and mp3 support enabled.

 Visit here fro more info
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by dcstar on 2007-01-06
> **ArmchairAthlete said:**
> That's it, how do I make firefox play embedded mp3s? I need my ytmnd sites to work properly =). 

I thought it would be simple but after a little searching I can't find the right plugin. Maybe I'm blind.

You may want to install the mozplugger package.

---

### Post by strabes on 2007-01-07
Do these three commands:```
cd /usr/lib/firefox/plugins/
sudo rm libtotem*
sudo apt-get install mplayer mozilla-mplayer
```

Basically you're removing all the totem firefox plugins, which are bad, and installing the mplayer one, which is good.

---

### Post by ArmchairAthlete on 2007-01-07
I installed mozilla-mplayer extension (seemed a lot easier than installing the plugin, which had a compile error when I finally got to running make), mozplugger, this... stuff "sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui", etc. 

Restarted firefox... still doesn't work and asks me to look for a plugin which it cannot find.

---

### Post by drpaul on 2007-01-07
check about:plugins in Firefox. It should have a quicktime plugin as part of the mplayerplugin

If not reinstall the mplayer plugin. It is the quicktime plugin that plays the sound from that page you referenced.

Paul

---

### Post by myke on 2007-03-04
I'm having the same problem.   I have flash files playing fine along with embedded vid files but mp3 files will not play embedded in firefox.   For instance, when I try to sample a ringtone that I might want to download with the preview being in mp3 format, it pops up a window that says "no video found".   I have mozplugger, mplayer plugin, and vlc plugins installed but non in any combination work with providing embedded mp3 support within firefox.  

**Correction:   I was able to get the mp3 support working by uninstalling mozplugger & the VLC plug-in and re-installing the mplayer plug-in.   Apparantly, must have been a conflict with more than one plug-in trying to handle the same extention.  Either way, it seems to be working now!**

---

### Post by diablo75 on 2007-11-02
I am having a similar problem with my website.  Here's an example URL:

[http://www.davestechsupport.com/faq/why_should_i_use_ubuntu.html](http://www.davestechsupport.com/faq/why_should_i_use_ubuntu.html)

And below is a little extra info about the plugins I have installed on my firefox:

```
zeke@zeke-desktop:~$ cd /usr/lib/firefox/plugins
zeke@zeke-desktop:/usr/lib/firefox/plugins$ ls
flashplugin-alternative.so  mplayerplug-in-dvx.so   mplayerplug-in-rm.so   mplayerplug-in-wmp.xpt
libflashplayer.so           mplayerplug-in-dvx.xpt  mplayerplug-in-rm.xpt  mplayerplug-in.xpt
libjavaplugin.so            mplayerplug-in-qt.so    mplayerplug-in.so
libunixprintplugin.so       mplayerplug-in-qt.xpt   mplayerplug-in-wmp.so
zeke@zeke-desktop:/usr/lib/firefox/plugins$ 

```

Any ideas?  Perhaps it has something to do with the way the HTML is written in the site?

---

