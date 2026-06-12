---
title: "Gray boxes with Flash"
date: 2008-02-08
forum: General Help
---

### Post by kevindubrow on 2008-02-08
Hi, very frequently now there is just a gray box where a flash app would be...say game or movie player. Its getting very annoying because restarting Firefox or my computer won't solve the issue.

I am running Ubuntu Studio 64bit and I believe I have gnash (but I'm really not sure). Does anyone know how to fix this? I would be glad to provide some more information if anyone needed it.

(by the way, I usually still hear the audio of the flash app even though the visuals are gray)

---

### Post by jan quark on 2008-02-08
type
```

about:plugins
```

into the browser, where you normally type in the [http://www](http://www). sites location

what plugins are enabled there?

---

### Post by kevindubrow on 2008-02-08
This is what I get:

(event.ctrlKey) { this.selected = null; return; } if (event.target == this) this.selected = null else this.selected = event.target; ]]>                PK &#65533;&#65533;&#65533;&#65533;&#65533;Oh0Ý°Ô6&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;content/global/dummyWindow.xul PK &#65533;&#65533;&#65533;&#65533;&#65533;a³1ÓgÑ&#65533;&#65533;Ñ&#65533;&#65533;&#65533;&#65533;&#65533;content/global/plugins.html  var strBundleService = Components.classes["@mozilla.org/intl/stringbundle;1"].getService(Components.interfaces.nsIStringBundleService); var pluginsbundle = strBundleService.createBundle("chrome://global/locale/plugins.properties"); var regionbundle = strBundleServ

---

### Post by kevindubrow on 2008-02-08
But that seemed very odd and I noticed that I had to restart Firefox because it just updated, but here is what I get now:

Shockwave Flash
Totem Web Browser Plugin 2.20.0
Windows Media Player Plug-in 10 (compatible; Totem)
DivX® Web Player
QuickTime Plug-in 7.2.0

---

### Post by forrestcupp on 2008-02-08
I think Gnash only supports Flash extensions up to version 7, and Flash is up to version 9 now.  Maybe the Flash apps are using extensions that Gnash doesn't support.

Good luck getting flashplugin-nonfree working in 64-bit.

---

### Post by kevindubrow on 2008-02-08
Gah...thats no fun. Thanks for the help though.

---

### Post by Doughsay on 2008-02-09
I'm having the same problem here, I'm running Ubuntu 64bit as well.  flashplugin-nonfree works fine.... sometimes.  But other times is produces gray boxes.  But usually, the gray boxes only appear a few seconds AFTER the flash movie is already playing.  So I can see the flash application for a few seconds, then it all goes gray and the flash context menus disappear.

I had installed flashplayer from the repos, but then tried to install straight from adobe's website.  Didn't help the problem...

Any ideas?

---

### Post by toupeiro on 2008-02-12
I get the same thing -- and tolerate it as long as I can.  I would just downgrade to 32-bit ubuntu except I have application and resource needs which require 64-bit. The other thing I get randomly with flash enabled pages (which is the vast majority of all pages these days) is the whole firefox session will freeze and three npviewer.bin boxes will pop up that are also locked which I have to kill.  

This is actually a pretty big killer -- and I know the problem ultimately lies with Adobe for not supporting 64 bit (hello? get with it, Adobe.  Even windows plays 64-bit in todays world)

I've tried several different "how to get flash to work in 64-bit ubuntu" tutorials, as well as hacked on it myself, but they have all led to this kind of performance which is, pardon the splitting of hairs, not what I would define as working fine or working at all.  

Has anyone found a real fix or 'functional workaround 'to these problems, or has a link to someone elses methodology to fix these problems that actually works?  I'm sure you'd be hero of the day if you would share your knowledge!

Many thanks!

---

### Post by fuji on 2008-02-14
Count me as one affected by this too.

There was a project on these forums that helped install a 32bit compiled Firefox, nsplugin and flash all 32bit.  They said we could delete it since gutsy fully supported flash on amd64.  I think this might be the only work around.  One day, when I have a bit more time I may try this.  As it is right now, there isn't really any flash sites I _must_ view so it's not a priority for me.


EDIT: Okay, I was bored, and the author Kilz made it so easy

Use this thread and ensure you're using the r48 script (which was recommended) - Turns out the latest version is very buggy.

[http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+amd64+firefox](http://ubuntuforums.org/showthread.php?t=476924&highlight=flash+amd64+firefox)

---

### Post by carpex on 2008-03-24
Description of the bug:
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/184157)

Excerpt:

 > This bug should only affect 64-bit SMP/SMT machines (i.e. multicore, multiprocessor, including presumably Intel HyperThreading).

The nspluginwrapper author has provided a patch: [http://launchpadlibrarian.net/11055616/npw.gthreads.diff](http://launchpadlibrarian.net/11055616/npw.gthreads.diff)

And Rashad Tatum built a fixed package: [http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb](http://launchpadlibrarian.net/11224902/nspluginwrapper_0.9.91.5-1ubuntu2_amd64.deb)

This worked for me ;-)
CP

---

### Post by kevindubrow on 2008-03-24
Thanks so much, but I got the .deb and tried to install it, but apparently I have a later version of whatever program this is...but I still have the gray box issue. Do you happen to know whats up with that?

---

### Post by carpex on 2008-03-25
All I had to do is to install the nspluginwrapper deb on top of what I already had and it did the job for me. 

CP

---

### Post by TommyIndep on 2008-06-19
I have the same problem as kevindubrow! Anybody know a solution to this? It's really annoying!

---

### Post by BilliShere on 2008-07-19
I still encounter this problem ... got a 64 bit processor but not running a 64 bit os. 32 bit hardy here.  i guess ill have to try out the newest flash betas

---

