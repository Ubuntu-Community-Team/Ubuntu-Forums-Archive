---
title: "Error when playing runescape with firefox"
date: 2007-10-21
forum: General Help
---

### Post by madtaz on 2007-10-21
Hi I'm sorry if I have put this in the wrong section.  When I first installed Ubuntu 7.10 I let my son play online adventure game.  A window popped up saying I had to install a add on, so I installed java console 6 I think or something like that.  The game then came on and my son played it.  Then the next day he tried to play the game a message comes up on a white back ground saying Error loading tepplet.  What does this mean or how do I correct it please someone help.

Madtaz

---

### Post by sajro on 2007-10-26
Hmm...,I never had that problem. First time I tried to install plugin, said I needed Manual Install. So I installed from manager, but didn't work.

Then I uninstalled Java from Add/Remove, reinstalled it and now RS works fine.

Hope I helped!

---

### Post by mig5 on 2007-11-02
> **madtaz said:**
> Hi I'm sorry if I have put this in the wrong section.  When I first installed Ubuntu 7.10 I let my son play online adventure game.  A window popped up saying I had to install a add on, so I installed java console 6 I think or something like that.  The game then came on and my son played it.  Then the next day he tried to play the game a message comes up on a white back ground saying Error loading tepplet.  What does this mean or how do I correct it please someone help.

Madtaz

Hi.  I think you may have installed the GCJ java plugin, which wasn't able to run the runescape applet last time I tried.  You need to close firefox, remove GCJ in Synaptic Package Manager (search for gcj and remove the appropriate packages) and then search for and install sun-java6-plugin .
After doing that, start firefox and type this into the address bar:
```
about:plugins
```
Check on the page that it loads to see whether the plugin is listed.
If it is then you should be able to play runescape in the normal manner.
As a side note, you may want to consider doing the following to stop runescape loading from scratch every time you play:
Make a folder in /home/[username]/ called .file_store_32 and another called .jagex_cache_32 . Once you've done that make sure you are selecting 'signed applet with default java' on the runescape detail select screen, and the game should load much quicker.

---

### Post by Xusn96 on 2008-04-16
TY so much Mig5 ... i have been sporadically trying to find out why runescape wouldnt load on this old box.  your the first poster i have seen to suggest the about : plugins command.  i have read many many posts about "just load up Sun JAva 6 and it will work" ... but aparrently everyone assumes you know you also have to remove any other version of java.  

My plugins revealed both sun java 6 and GCJ, removed GCJ with synaptic and now runscape loads and runs great. KUDOS to you!!

 My youngest will be pleased and this Old Pentium II 400 will be put to some amount of use ... running Unbuntu of course.

X out.

---

