---
title: "Firefox 91 won't work with previous profile"
date: 2021-08-12
forum: General Help
---

### Post by Keith_Helms on 2021-08-12
Firefox crashed on me today and when I restarted it, it came up without my bookmarks toolbar (or it didn't display any of the links).   It would not go to any websites.  Type in something like cnn.com in the search bar and nothing happens.  Select a bookmark from the menu and nothing happens.  I tried restarting it in safe (now troubleshoot) mode and that didn't help either.

I created a new profile and that DID get it working.  I then downloaded and unpacked the previous version - 90.0.2  - in a directory and executed firefox from there and forced it to allow use of an older profile with MOZ_ALLOW_DOWNGRADE=1.  When I selected the profile that won't work under v91, it works correctly under 90.0.2.

So I have two choices now, 1) I can continue to run version 90.0.2 with my profile that has all my extensions, customizations, and option settings, or 2) I can move to the new version with a new profile and reconfigure everything.  If I hadn't been able to start up the old profile using an older version I wouldn't even have been able to export settings for plugins like noscript.

It would be nice if they could fix this problem so I can allow firefox updates to continue.

---

### Post by TheFu on 2021-08-12
> **Keith_Helms said:**
>  
It would be nice if they could fix this problem so I can allow firefox updates to continue.

Don't hold your breath for Mozilla to do anything.  Last year, I was forced to start a fresh profile. I'd been bringing the old one forward for perhaps a decade. There are just some settings that break code and they have little interest in creating a settings cleaner, from what I've seen.  Took me a few weeks to find all the little settings that were lots due to this forced change.  

For example, firefox blocks accessing administrative websites on non-standard ports unless there is an override manually added for those ports.  

I don't support IPv6 and all my systems disable it for security reasons. That freaked out firefox.  There's a setting to disable IPv6 - they don't just check the OS and see it isn't there.  Frustrating.  Addons were the trivial part of the migration for me. It is more about all the about:config settings that have been lost to me.

---

### Post by monkeybrain20122 on 2021-08-12
It is strange. My upgrade to FF91 is seamless across several machines with Ubuntu 20.04 and Kubuntu 20.04. In fact on the intel machine with Ubuntu 20.04 vaapi now works a lot more efficiently, before gpu use was always < 10% now it reaches > 30% for intense videos and 0 frame drop.

---

### Post by TheFu on 2021-08-12
> **monkeybrain20122 said:**
> It is strange. My upgrade to FF91 is seamless across several machines with Ubuntu 20.04 and Kubuntu 20.04.

how old was your firefox profile?  Was it fresh in 20.04 or have you been bringing it forward since 2005 like some of us?

---

### Post by monkeybrain20122 on 2021-08-12
> **TheFu said:**
> how old was your firefox profile?  Was it fresh in 20.04 or have you been bringing it forward since 2005 like some of us?


All from 20.04, but they went through quite a few FF updates.

---

### Post by Keith_Helms on 2021-08-12
My profile is probably fairly ancient.   I think I had to force a Firefox update to continue using it once in the past.  Yes, it's hard to remember all the little tweaks I've made over the years.  For example, I HATE autoplay video so I had gone through the config settings and turned off every media type I could find.   When I get to the point where a video shows as "Video not available.  Unfortunately, this video is missing or damaged..." then I'm happy.  I can always play a video under Chrome or a different Firefox profile if I want to see it. :P

---

### Post by monkeybrain20122 on 2021-08-12
> **Keith_Helms said:**
> My profile is probably fairly ancient.   I think I had to force a Firefox update to continue using it once in the past.  Yes, it's hard to remember all the little tweaks I've made over the years.  For example, I HATE autoplay video so I had gone through the config settings and turned off every media type I could find.   When I get to the point where a video shows as "Video not available.  Unfortunately, this video is missing or damaged..." then I'm happy.  I can always play a video under Chrome or a different Firefox profile if I want to see it. :P

Actually it seems it hasn't been autoplaying videos for quite a while. I remember I had to tweak an option in about:config to disable it a while back but I haven't been doing that for quite some times. Well if your profile is very old I am sure some configuration settings might have changed or deprecated, so I tend not to migrate my profile on OS update, just restore the bookmarks and tabs and I would retewak everything.

But then my profile is very simple. I am a simple person. :)

---

### Post by Keith_Helms on 2021-08-12
> **monkeybrain20122 said:**
> Actually it seems it hasn't been autoplaying videos for quite a while. I remember I had to tweak an option in about:config to disable it a while back but I haven't been doing that for quite some times. Well if your profile is very old I am sure some configuration settings might have changed or deprecated, so I tend not to migrate my profile on OS update, just restore the bookmarks and tabs and I would retewak everything.

But then my profile is very simple. I am a simple person. :)

There is a setting under privacy -> permissions that supposedly allows you to set autoplay to "Block Audio and Video", but that doesn't work all the time.  Turn it on, then go to yahoo.com and you'll see some moving images down the left side of the page.

---

### Post by monkeybrain20122 on 2021-08-13
> **Keith_Helms said:**
> There is a setting under privacy -> permissions that supposedly allows you to set autoplay to "Block Audio and Video", but that doesn't work all the time.  Turn it on, then go to yahoo.com and you'll see some moving images down the left side of the page.

Actually I haven't changed the setting. It is default "block audio". I remember it was always the audio autostart that bothered me, the images not so much. I could always kill them, it is the f-ing audio that caught me by surprise. So maybe that's why I wasn't thinking about it for a while.

---

### Post by TheFu on 2021-08-13
> **monkeybrain20122 said:**
> All from 20.04, but they went through quite a few FF updates.

1 yr?  Hah!  That's nothing.  Imagine all the updates that happened from 2010 until today.
About 18 months ago, FF broke a bunch of my internal websites when they started using an external DNS-over-HTTPS by default.  I've run my own LAN DNS for a while and before that, local /etc/hosts were used to make internal websites work. Attempts to protect the clueless by default cause problems for people like me.

When the internet is down, I may not notice for hours, because most of my access is to LAN servers that pull and cache information every few hours.

---

### Post by monkeybrain20122 on 2021-08-13
> **TheFu said:**
> 1 yr?  Hah!  That's nothing.  Imagine all the updates that happened from 2010 until today.
About 18 months ago, FF broke a bunch of my internal websites when they started using an external DNS-over-HTTPS by default.  I've run my own LAN DNS for a while and before that, local /etc/hosts were used to make internal websites work. Attempts to protect the clueless by default cause problems for people like me.

When the internet is down, I may not notice for hours, because most of my access is to LAN servers that pull and cache information every few hours.

Imagine 2010? I was still on  Windows XP, then installed Ubuntu 10.04 in 2011 and wifi didn't work. Took a lot of googling and finally it worked, yay. Man that was a long time ago. I have gone through a lot machines and OSes since then, broke up with a few people and changed jobs several time, a few people I knew back then have passed away ... do you think I would still keep my FF profile? :)

---

### Post by TheFu on 2021-08-13
> **monkeybrain20122 said:**
> Imagine 2010? I was still on  Windows XP, then installed Ubuntu 10.04 in 2011 and wifi didn't work. Took a lot of googling and finally it worked, yay. Man that was a long time ago. I have gone through a lot machines and OSes since then, broke up with a few people and changed jobs several time, do you think I would still keep my FF profile? :)

I kept mine.  Bringing config files forward from prior OS installs is a critical part of my restore process.

---

### Post by ajgreeny on 2021-08-13
> **TheFu said:**
> I kept mine.  Bringing config files forward from prior OS installs is a critical part of my restore process.
Same here.
My profile has been passed from machine to machine and from Ubuntu (Xubuntu) version to new version for more years than I can remember.
I do not synchronise my bookmarks etc etc, through the firefox settings option, but simply move them all manually.

The only major problem I have ever seen doing this is trying to open an older version of firefox using a profile that has already been used on a newer version of firefox; that causes an error informing that a new profile must be created and in this situation there seems to be no way to override this.
I simply can see very little sense in this and wish there was a way to override this requirement (after backing up the profile) and then, if it is corrupted by the older firefox version a new profile can be created.

My main moan about firefox 91 has been the change, yet again, to the GUI, that I had managed to get just as I wanted it following the release of firefox 89 by editing many ***about:config***  entries (mainly disabling proton) and using a ***userChrome.css*** file to make many other changes.  See my thread at [https://ubuntuforums.org/showthread.php?t=2465839](https://ubuntuforums.org/showthread.php?t=2465839)

---

### Post by Keith_Helms on 2021-08-13
> **ajgreeny said:**
> 
The only major problem I have ever seen doing this is trying to open an older version of firefox using a profile that has already been used on a newer version of firefox; that causes an error informing that a new profile must be created and in this situation there seems to be no way to override this.


Actually, you CAN get around this.   You need to start Firefox from the command line and set an environment variable to allow using a profile marked by a newer release.

```
MOZ_ALLOW_DOWNGRADE=1 firefox -P 
```

---

### Post by ajgreeny on 2021-08-13
Thanks Keith; I'll try that next time should I need or want to downgrade a firefox installation.

---

