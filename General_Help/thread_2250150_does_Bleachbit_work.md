---
title: "does Bleachbit work?"
date: 2014-10-27
forum: General Help
---

### Post by linux.smurf on 2014-10-27
I am running xubuntu for my single core, and i use bleachbit to clean my hard drive etc. but everything runs slow, takes more time for apps to open like firefox or vlc. What can I do to make run like new without having to wipe out and re-install...

And I am new as well so I do thank You in advance

---

### Post by richierich1986 on 2014-10-27
The reason it is slow is probably more related to it running on a single core and perhaps an hdd instead of ssd? That is quite limited hardware, although it depends on what kind of single core you're using, because a Pentium might still be decent if it's powerfull enough. But first and foremost: Don't use Bleachbit!!! 

I have used it myself for years without realizing that it was the reason all my Linux installs got unstable etc after a while. I haven't used it since my latest install and that has been running stable and quick for six months now! Unprecedented on my computers! And it isn't really necessary anyway. 

It was just a leftover from my Windows-mindset, which told me to always keep cleaning (Ccleaner addiction). But since a linux install usually doesn't clutter that much if at all, it is a complete waste of time and made my install super unstable. I finally got out of that mindset and learned to let go. A linux install doesn't take up as much space as a Windows 7 or 8 install anyway.

The only thing I do now and then after I've installed something is:

[B]sudo apt-get autoremove && sudo apt-get autoclean

[/B]The first part uninstalls unused leftover dependencies from software you've previously uninstalled and the second part removes leftover installation packages for that software.

Oh, and I also from time to time go to my home folder, press ctrl+h to see hidden folders and go through .config, .gconf and .local folders to delete folders for software that I myself deliberately deleted, but only if the folder carries the name of the deleted software and only if I'm sure nothing else depends on it.

---

### Post by linux.smurf on 2014-10-27
Thank You for replying, it was most helpful. (5 stars)

---

### Post by ibjsb4 on 2014-10-27
I have to give it 3 stars.
Bleachbit has been around for years and has stood the test of time.  I started using it in 2008 when I was new to linux.  IMO its a great tool for beginners.  As time passes, you will probably use it less to not at all.  Replacing it with your own cleaning methods.

Because a package does not work for one, it does not mean its bad for all.  A rule of thumb with bleachbit; if you get a popup (warning) when checking what to clean, then do not use that option.  Also look closely at browser (www) cleaning options.

---

### Post by slickymaster on 2014-10-27
*Moved to the ***General Help*** sub-forum*

---

### Post by Mike_Walsh on 2014-10-27
I, too, run an Athlon 64, along with a 160 GB HDD, and 3 GB of RAM. I don't consider it to be slow at all; it WHOOPS my old Dell laptop (intel 'Netburst' Celeron); 128k cache (!), and no SSE3's.....SLOOOOOW.

Mind you, I ran XP on that thing for over 10 years, so I guess anything would seem fast in comparison! I don't use my 'puter for anything that really requires fast response times.....mainly graphic design, and CAD work; which I take at my own pace.That , and listening to music while I work, and a bit of web browsing; it multitasks nicely, for what I ask of it.

But then I guess us 'oldies' are used to taking life at a slightly slower pace..! ;)

BTW, I wouldn't touch Bleachbit with a bargepole...

Regards,

Mike.

---

### Post by MartyBuntu on 2014-10-27
You realise you're probably also erasing *cached* files when you run BleachBit, right?
That's why some applications seem to run slow, or slower *after* you run it.

---

### Post by rbmorse on 2014-10-27
I use Bleachbit as part of my weekly maintenance routine, mostly to deal with the accumulation of old, no longer needed cache and log files.  Never a problem in more than four years that couldn't be traced back to stupid user tricks.

---

### Post by richierich1986 on 2014-10-28
I found this useful page, if you don't want to use bleachbit. It also
explains each action so you can decide if you think it necessary or not.

[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

---

### Post by speartip on 2014-10-28
IMO Bleachbit is an excellent tool. I have been using it for years without the stabilty of my system being affected. You just need to be selective in what it cleans.
For eg. I leave unticked, all the deep scan options, & anything that gives a warning. Also be careful about cleaning any passwords you save, otherwise you will need to reenter them all.
 You can also whitelist any folders you don't want wiping in the preferences.
 I clean about 1 gig of crud per month using Bleachbit, never an issue.

---

### Post by mdavis1231 on 2015-03-27
I'm uninstalling BleachBit because everytime I use it, I have problems with my video thumbnails.  I have to go through this entire rigamaroll go get them back.  Plus, it resets the order of the messages in my Thunderbird back to oldest messages shown first and newest messages shown last.  Then I have to go into Thunderbird and reset everything every time I use BleachBit.  And those are only the things that I've noticed.  NO THANKS.

---

### Post by poorguy on 2015-07-13
i only use bleachbit to clean firefox browser and nothing else. all boxes are checked in firefox browser to be cleaned and so far all is good. i don't use bleachbit all that often maybe once every 90 days. from what i have read on this forum and other web searches is that linux doesn't get all full of crap that needs to be cleaned.

---

### Post by monkeybrain20122 on 2015-07-13
> **richierich1986 said:**
> I found this useful page, if you don't want to use bleachbit. It also
explains each action so you can decide if you think it necessary or not.

[https://sites.google.com/site/easylinuxtipsproject/clean](https://sites.google.com/site/easylinuxtipsproject/clean)

It is a very opinionated, alarmist page and  I tend to ignore people like that even when I was a newbie (now there is even clearer that he is full of it) I have used bleachbit since 10.04 and never had a problem which is not due to my own stupidity (once). 

Yes you can run all these commands manually on the terminal but what is the advantage of doing all the typing for a dozen of commands separately and wasting brain cells remembering each command instead of having a convenient gui to do them all at once?  For example the first thing I do after a new Ubuntu install would be to get rid of all the useless localisations which take up several hundreds of Mb of disk space. Why do I want 20 different language packages in my system which I will never use?

My advice is, don't check an option on bleachbit if you don't know what it does and google to look for explanations if the documentations contain words that you don't understand. It is just common sense. Bleachbit is very good in that all boxes are unchecked when you first install it.

---

### Post by monkeybrain20122 on 2015-07-13
> **poorguy said:**
> i only use bleachbit to clean firefox browser and nothing else. all boxes are checked in firefox browser to be cleaned and so far all is good. i don't use bleachbit all that often maybe once every 90 days. from what i have read on this forum and other web searches is that linux doesn't get all full of crap that needs to be cleaned.

Actually Firefox does get slow if a lot of junks get accumulated. I uncheck session because I keep many tabs open. Some people may not want to clear passwords or history either.

---

### Post by monkeybrain20122 on 2015-07-13
> **mdavis1231 said:**
> I'm uninstalling BleachBit because everytime I use it, I have problems with my video thumbnails.  I have to go through this entire rigamaroll go get them back.  Plus, it resets the order of the messages in my Thunderbird back to oldest messages shown first and newest messages shown last.  Then I have to go into Thunderbird and reset everything every time I use BleachBit.  And those are only the things that I've noticed.  NO THANKS.

Just don't check system > cache, it is where the thumbnails are stored. 

That box is unchecked in freshly installed bleachbit which means you checked it yourself. If you don't know what is in there why did you check it? It proves that the problem is the user rather than the program which does exactly what it is supposed to do and does exactly what you tell it to.

Also you may not want to clear bash history if you want to remember commands you have run.

---

### Post by monkeybrain20122 on 2015-07-13
But going back to OP I don't think cleaning or not would make a  big difference for performance in general (Firefox would speed up though in my experience) It could be that for some operations that the cache need to be regenerated as someone said above (e.g thumbnails in document folder) Firefox cache is different, it contains a lot of old stuffs you don't need to regenerate but take up time to preload apparently.

---

### Post by VMC on 2015-07-13
> **monkeybrain20122 said:**
> It is a very opinionated, alarmist page and  I tend to ignore people like that even when I was a newbie (now there is even clearer that he is full of it) I have used bleachbit since 10.04 and never had a problem which is not due to my own stupidity (once). 

Yes you can run all these commands manually on the terminal but what is the advantage of doing all the typing for a dozen of commands separately and wasting brain cells remembering each command instead of having a convenient gui to do them all at once?  For example the first thing I do after a new Ubuntu install would be to get rid of all the useless localisations which take up several hundreds of Mb of disk space. Why do I want 20 different language packages in my system which I will never use?

My advice is, don't check an option on bleachbit if you don't know what it does and google to look for explanations if the documentations contain words that you don't understand. It is just common sense. Bleachbit is very good in that all boxes are unchecked when you first install it.
I read that link a while back and thought nothing of it. I also get rig of the localization's. That's the big one. Hundreds of MB are recovered.
> **monkeybrain20122 said:**
> Actually Firefox does get slow if a lot of junks get accumulated. I uncheck session because I keep many tabs open. Some people may not want to clear passwords or history either.
Agree.
> **monkeybrain20122 said:**
> Just don't check system > cache, it is where the thumbnails are stored. 

That box is unchecked in freshly installed bleachbit which means you checked it yourself. If you don't know what is in there why did you check it? It proves that the problem is the user rather than the program which does exactly what it is supposed to do and does exactly what you tell it to.

Also you may not want to clear bash history if you want to remember commands you have run.I keep all my bash history around. And from time to time I can awk-compress it. Try this:
```
wc .bash_history
```
then
```
awk '!x[$0]++' .bash_history|wc
```

---

### Post by poorguy on 2015-07-13
ok so you don't run the session clean because you keep tabs open, are these tabs open when you are doing a clean or closed when you are doing a clean. i was under the impression that all open windows should be closed before running bleachbit, however i maybe wrong about that. i just don't see any need in my case to bleachbit any more than my firefox browser as i don't ever seem to have any warnings or messages about running low on hard drive space. i could see the need if i only had a 20 gb hard drive.

---

### Post by monkeybrain20122 on 2015-07-13
> **poorguy said:**
> ok so you don't run the session clean because you keep tabs open, are these tabs open when you are doing a clean or closed when you are doing a clean. i was under the impression that all open windows should be closed before running bleachbit, however i maybe wrong about that. i just don't see any need in my case to bleachbit any more than my firefox browser as i don't ever seem to have any warnings or messages about running low on hard drive space. i could see the need if i only had a 20 gb hard drive.

FF has to be closed when cleaning, but the tabs are not closed or it will defeat the purpose. :) When restart FF the tabs are still there. FF loads tabs only when you click that's why it can keep a lot of tabs without ram going through the roof (like Chrome)

---

### Post by poorguy on 2015-07-13
ok so if i have the session box checked when i clean i am losing as related to the tabs / the cache or cookies for the tabs or would the tabs just load slower since they were cleaned out. hate to be a dumb ass but i am missing something perhaps. i am seeing tabs as places that i saved or added like bookmarks. i also run with several tabs as i call them or several windows open most of the time.

---

### Post by monkeybrain20122 on 2015-07-14
> **poorguy said:**
> ok so if i have the session box checked when i clean i am losing as related to the tabs / the cache or cookies for the tabs or would the tabs just load slower since they were cleaned out. hate to be a dumb ass but i am missing something perhaps. i am seeing tabs as places that i saved or added like bookmarks. i also run with several tabs as i call them or several windows open most of the time.
  
No, if you check the session box then the tabs will be gone. There is a file called sessionrestor.js in ~/.mozilla/firefox/somethingsomethingdefault/ (the file comes into existence only when firefox is not running so to see it have to close FF) If you check the box that file gets removed and all your tabs will be gone. (Conversely if you have a new install of Firefox on a different machine, say, copy that file to its ~/.mozilla/firefox/default folder will bring all your tabs over)

---

### Post by poorguy on 2015-07-14
ok i believe i have got it. i don't tab stuff i only bookmark and so i have never lost any book marks. sometimes the granite around my little brain gets in the way. thanks.

---

