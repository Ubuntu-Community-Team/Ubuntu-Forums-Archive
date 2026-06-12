---
title: "Firefox crashes in Gutsy"
date: 2007-10-19
forum: General Help
---

### Post by muecker on 2007-10-19
Since upgrading to Gutsy yesterday, I can no longer use Firefox for many sites.  It worked fine under Feisty and never crashed, but as soon as I rebooted the first time after upgrading it crashed.  Here are some specific examples:

 - Google Mail crashes when Google Chat finishes connecting.
 - A web site with flash will crash it every time (e.g. [http://cbs4denver.com](http://cbs4denver.com))

I completely reinstalled Firefox yesterday and got it to work for a while.  This morning when I got to work my machine had rebooted overnight (I'm not sure why) and Firefox stopped working again.  I'm not sure if this is related to Xinerama, after getting Firefox to work I was playing with my xorg.conf trying without any success to get dual head to work using ATI's pairmodes instead of Xinerama.  I finally gave up and switched back to the dual head xorg.conf set up by Gutsy and have not got Firefox working again.

I'm running the 32-bit Gutsy on a Thinkpad T60.  I upgraded from Feisty yesterday afternoon.

---

### Post by muecker on 2007-10-19
I have it working, at least for now.  I renamed my .mozilla directory and let Firefox come up with a new profile.  I had to reinstall all of my plugins and set up everything again, but it hasn't crashed yet.

---

### Post by deformation on 2007-10-19
i have the same exact problem.

---

### Post by nuclearj on 2007-10-19
> **muecker said:**
> 
 - Google Mail crashes when Google Chat finishes connecting.
 - A web site with flash will crash it every time (e.g. [http://cbs4denver.com](http://cbs4denver.com))



I have the same problem too!  What did you rename your folder to?  Could you explain what you did step by step?  Thanks!

---

### Post by muecker on 2007-10-20
Just rename ~/.mozilla to anything you want.  I called mine .mozilla.old.  Once Firefox creates a new profile, shut it down and you can copy your old bookmarks.html into the new profile and have your bookmarks back again.

---

### Post by kyllikki on 2007-10-20
No need to create a new profile, I just purged the contents of my ./mozilla/plugins folder and that seemed to fix the problem.  I believe the problem was caused by the flash plugin.

---

### Post by nuclearj on 2007-10-22
> **kyllikki said:**
> No need to create a new profile, I just purged the contents of my ./mozilla/plugins folder and that seemed to fix the problem.  I believe the problem was caused by the flash plugin.

Just rename ~/.mozilla to anything you want. I called mine .mozilla.old. Once Firefox creates a new profile, shut it down and you can copy your old bookmarks.html into the new profile and have your bookmarks back again.



I did both of these things and it did not fix the problem.  I'm using feisty by the way.  Also I do not have a .mozilla/plugins folder.  I'll see if I can find the flash plugin and delete it.  If anyone else has some insight i am open cause this is an annoying problem.  Thanks in advance!

SOLVED!!!!

I found a plugins folder in /usr/lib/mozilla-firefox/plugins

I deleted libflashplaer.so by doing this:
```
/usr/lib/mozilla-firefox/plugins$ sudo rm libflashplayer.so
```
(which i am very proud of myself for doing because it means that things are beginning to make sense after months and months of bumping my head on things)

I opened a flash page and firefox indicated the plugin was missing.  I installed flash again, restarted firefox, and viola!  It worked!

---

### Post by eosha on 2007-10-22
I tried that, but it didn't work. I can get to Ubuntuforums and a few other websites, but many others (Gmail, for example) crash firefox every time.

---

### Post by sahilsapre on 2007-10-29
i think it's got something to do with gmail chat...log in from another browser, and use the gmail view: standard without chat...now if you log back in from firefox, it shouldn't crash..it didn't for me, at least..that should solve your gmail problem at least..

---

