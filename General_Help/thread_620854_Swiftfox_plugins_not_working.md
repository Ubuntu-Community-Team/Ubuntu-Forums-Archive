---
title: "Swiftfox plugins not working"
date: 2007-11-23
forum: General Help
---

### Post by werewolves on 2007-11-23
I'm having a problem with Swiftfox on Gutsy.

I installed using the instructions here: [http://getswiftfox.com/debian.htm](http://getswiftfox.com/debian.htm)

The problem is that no plugins work.  They all work in Firefox (mplayer, flash, totem, etc), but nothing happens in Swiftfox.  "About plugins" in Swiftfox shows all of them installed.  The Swiftfox plugins directory seems to be a link to the Firefox plugins directory.

I am getting these type of errors when I run Swiftfox from the command line:

```
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so [/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]
```

Any ideas??

---

### Post by werewolves on 2007-11-30
Bump, any ideas?

---

### Post by dgtlchlk on 2007-12-16
I get the same errors on the latest build of Swiftfox, 2007121620, 3.0b3pre.
Both Firefox and Swiftweasel pick up the plugins just fine. Anyone know whats different in Swiftfox that stops them from loading correctly?

---

### Post by jbman on 2007-12-16
the new version 3 is not working correctly with plugins made for 2. I am using the nightly builder plugin which gives the option to stop swiftfox checking for plugin compat. i have found all my plugins work this way.

---

### Post by p_quarles on 2007-12-16
This happens in Gutsy AMD-64. The problem, I discovered, is that Ubuntu installs Flash with the NSPluginwrapper by default. The AMD-64 version of Swiftfox is, strangely enough, a 32-bit compilation of the Firefox source code, which means that the two won't work together without further configuration. 

My solution was to install Swiftweasel, customized for my processor. It has no problem inheriting your Firefox add-ons (except that it will reset the theme to its own default). 

If neither of you are running the 64-bit version, then I have no idea what the problem is.

---

### Post by dgtlchlk on 2007-12-17
Actually I have the latest Swiftweasel build for my Core 2 Duo on AMD64 Gutsy installed and it does pick up all my plugins but the Swiftweasel build is quite a bit older than Swiftfox and it lacks quite a few of the new features that have been added in the past month or so. Such as the new history drop down interface and better Places support.

Guess I'll just wait and hope for a new Swiftweasel build...

---

### Post by p_quarles on 2007-12-18
> **dgtlchlk said:**
> Actually I have the latest Swiftweasel build for my Core 2 Duo on AMD64 Gutsy installed and it does pick up all my plugins but the Swiftweasel build is quite a bit older than Swiftfox and it lacks quite a few of the new features that have been added in the past month or so. Such as the new history drop down interface and better Places support.

Guess I'll just wait and hope for a new Swiftweasel build...
Well, yeah, that's because you're using the beta version of Firefox 3's code. The majority of plugins and extensions haven't been updated for the new Gecko engine yet, so that's to be expected. 

Swiftweasel is up-to-date with the most recent stable release of Firefox, though. The OP didn't specify whether he/she was using 2 or 3.

---

### Post by dgtlchlk on 2007-12-18
Oh, I'm using the 3.0 beta builds of both Swiftweasel and Swiftfox. I realize the Swiftfox issue would be fixed by a true 64bit compile but I'm not gonna hold my breath for that.

---

