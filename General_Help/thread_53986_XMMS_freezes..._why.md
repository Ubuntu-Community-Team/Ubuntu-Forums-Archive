---
title: "XMMS freezes... why?"
date: 2005-08-03
forum: General Help
---

### Post by Shwiing on 2005-08-03
Well I went to Applications -> System Tools -> Add/Remove Programs.
I installed xmms, opened the program up, added some music files to the list,
pushed play and it froze.

Everytime I try to play anything it freezes... 

After that I uninstalled it and went to install it by myself from the xmms site, and still same thing...

Does anyone have a fix for this? or maybe a _better_ mp3 player?

thanks

---

### Post by serioussam on 2005-08-03
[QUOTE=Shwiing]Well I went to Applications -> System Tools -> Add/Remove Programs.
I installed xmms, opened the program up, added some music files to the list,
pushed play and it froze.

Everytime I try to play anything it freezes... 

After that I uninstalled it and went to install it by myself from the xmms site, and still same thing...

Does anyone have a fix for this? or maybe a better mp3 player?

thanks[/QUOTE]
 Yeah it freezes when i play too :(

---

### Post by kassetra on 2005-08-03
[QUOTE=Shwiing]Well I went to Applications -> System Tools -> Add/Remove Programs.
I installed xmms, opened the program up, added some music files to the list,
pushed play and it froze.

Everytime I try to play anything it freezes... 

After that I uninstalled it and went to install it by myself from the xmms site, and still same thing...

Does anyone have a fix for this? or maybe a _better_ mp3 player?

thanks[/QUOTE]

Do you have all of the codecs to play your music installed (i.e. gstreamer0.8-lame)?  If you don't have the codec installed before you try to play the file, sometimes it can cause xmms to lockup.  Have you tried typing xmms in a terminal window and seeing the information it spits out as you add files and try to play them?

Well, I prefer bmp, but that's simply because it's xmms with a gtk2 interface; sometimes though, I like zinf.  Other people enjoy rhythmbox which is an iTunes clone - still other people like Muine (another iTunes clone.)  Since I don't know what you prefer or like, I can't suggest an alternative player.

---

### Post by Shwiing on 2005-08-03
Thanks for the reply, I tried running xmms in terminal and it just hangs I dont even get an output. I tried downloading extra codecs and no luck. So I am pretty positive xmms doesnt work on my system, its a drag because appearantly everyone else with ubuntu got it working so it really doesnt make any sence at all in my opinion.

Thanks

---

### Post by Shwiing on 2005-08-03
So I installed bmp configure went fine, make and make install worked perfectly.

AND IT HANGS WHEN I TRY TO PLAY MUSIC!

AHhhh Im blowing off my head.

what is wrong with ubuntu!!!!

I didnt change any big settings, with a normal install.... is the newest release messed up?

Sorry im just really mad.

---

### Post by Shwiing on 2005-08-03
Ok so it could be that I dont have the right codecs but I tried tons and cant play the files still, do you have any suggestions for codecs for mp3 and wav?

---

### Post by Sam on 2005-08-03
In XMMS or BMP, go in the preferences and change the output plugin.

---

### Post by Shwiing on 2005-08-03
yay! thanks a bunch  :)

---

### Post by Shwiing on 2005-08-03
Is there any other plugin for output I could download because the one i switched to sounds really fuzzy.

Thanks

---

### Post by FreeJack on 2005-08-03
I've come accross with the same problem only i can't manage it whenever i reinstall xmms again i come accross with this
"Setting up acl-pro-installer (6.2.31) ...
Aborting
dpkg: error processing acl-pro-installer (--configure):
 subprocess post-installation script returned error exit status 1
Setting up xmms (1.2.10-2ubuntu1) ...

Errors were encountered while processing:
 acl-pro-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)"
now can some please explain to me what directory he means??? cause i'm sure have no idea

---

### Post by wh0rd on 2005-08-03
Check this post out, I had similar problems I switched the output to eSound Output Plugin.

on XMMS > Right Click > Options > Preferences > 
on the Audio I/O Plugins tab in the Output Plugin area select the eSoung Output Plugin. Click Apply. Click Okay. 

Then that did it no more XMM freezing when playing mp3s.  :grin: 

POST:
[http://www.ubuntuforums.org/showthread.php?p=285209#post285209](http://www.ubuntuforums.org/showthread.php?p=285209#post285209)

---

### Post by tom957 on 2005-08-25
You're the man!  :grin:

---

### Post by bujao on 2005-08-31
The plugin u switch to sounds really bad on my laptop(HP ze2229), The songs jump/hangs several seconds when u scroll a window for example. I would REALLY like another alternative plugin that works better.  :?

---

### Post by Mike-97470 on 2005-08-31
Switchinng to the eSound output plug-in fixed the freeze problem for me for BMP as well as XMMS.  And it sounds fine.

eSound Output Plugin 1.2.10 (libesdout.so)

---

### Post by mizako on 2005-09-01
[QUOTE=Mike-97470]Switchinng to the eSound output plug-in fixed the freeze problem for me for BMP as well as XMMS.  And it sounds fine.

eSound Output Plugin 1.2.10 (libesdout.so)[/QUOTE]
 I can not choose as my xmms output plugin the eSound Output Plugin just the OSS or the disk writer. How do i installed this new plugin?

---

