---
title: "Simple-ccsm  Error dependancy is"
date: 2008-04-25
forum: General Help
---

### Post by yogo on 2008-04-25
not satisfiable compizconfig settings manager.

I have uninsatalled and re-installed the compizconfig settings manager several times and still I always get this error. What am I missing or doing wrong to install the simple-ccsm and how can I get the compiz-fuzion icon so I can reload windows manager etc?

TIA

---

### Post by Zorael on 2008-04-25
As for the icon app, there should be a huge thread about that in the archive.

For instance, [http://ubuntuforums.org/showthread.php?t=601310](http://ubuntuforums.org/showthread.php?t=601310). Meant for Kubuntu, but shouldn't matter. Google~

As for the dependency error, could you give us the output of the following command, entered in a terminal?
```
$ sudo aptitude install compizconfig-settings-manager simple-ccsm
```
Would need to know the details, so copy and paste it.

---

### Post by yogo on 2008-04-25
[FONT=monospace]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find any package whose name or description matched "simple-ccsm"
The following packages have been automatically kept back:
  compiz-plugins libdecoration0 libk3b2 libpoppler-glib2 libpoppler2 libpq5 
  libxine1 libxine1-ffmpeg mencoder 
The following packages have been kept back:
  brasero compiz-core compiz-fusion-plugins-extra compiz-kde gpsd hpijs 
  hplip hplip-data k3b kaffeine libtheora0 ntfs-3g poppler-utils 
  startupmanager 
0 packages upgraded, 0 newly installed, 0 to remove and 23 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done  


As for the icon, I installed the icon but it is not working correctly, something is missing, when I double click the icon, my screen goes blank ie no task bars, desktop icons, just my desktop background is displayed for about four seconds then everything comes back to normal, but no app to choose windows decorators etc.

And I followed the thread you linked before it was linked here,

[http://ubuntuforums.org/showthread.php?t=601310](http://ubuntuforums.org/showthread.php?t=601310)

Any ideas?

TIA
[/FONT]

---

### Post by CarpKing on 2008-04-25
Sounds like simple-ccsm isn't in the repositories, at least under that name.  Try searching for Compiz in Synaptic; if it's in a repository listed in sources.list, it should show up there.

---

### Post by Zorael on 2008-04-26
simple-ccsm should be in the universe repositories, so make sure you've enabled those in Software Sources.

---

### Post by yogo on 2008-04-26
> **Zorael said:**
> simple-ccsm should be in the universe repositories, so make sure you've enabled those in Software Sources.


I do have universe enabled in Ubuntu software channel, do I need to enable something else in 3rd party software?

TIA

PS I do not have simple ccsm in Synaptic.

---

### Post by Zorael on 2008-04-26
Curious. [http://packages.ubuntu.com/hardy/simple-ccsm](http://packages.ubuntu.com/hardy/simple-ccsm) :<

I'm confused. In the original post you said it couldn't be installed due to dependencies not being satisfied, but now you say Synaptic can't find it? It is downloadable from that site, if you want to try it that way.

I haven't tried it, but there seems to be a package called fusion-icon in universe.

[http://packages.ubuntu.com/hardy/fusion-icon](http://packages.ubuntu.com/hardy/fusion-icon)

---

### Post by yogo on 2008-04-26
Zorael,

I have been using that link to install it, I always have the same error saying I do not have the compizconfig setting manager installed.

[http://i29.tinypic.com/a9n4gm.png](http://i29.tinypic.com/a9n4gm.png)

PS I am using Gutsy, will that be the reason why I am not finding them in Synaptic.

---

### Post by techlogix on 2008-11-24
For 8.10 - try this.

```


sudo apt-get install python python-central python-gtk2 python-compizconfig compizconfig-settings-manager

```

Then go to System>Preferences
 
You should see CompizSettings Manager.

Enjoy

---

