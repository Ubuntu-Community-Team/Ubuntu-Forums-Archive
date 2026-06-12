---
title: "How do I find out what version of Flash is installed on my computer?"
date: 2015-05-21
forum: General Help
---

### Post by Tom_Carr on 2015-05-21
How do I find out what version of Flash is installed on my computer?

---

### Post by monkeybrain20122 on 2015-05-21
11.2, not need to check. :) Adobe will not update flash version for Linux, but will provide security updates til 2017

If you need versions higher than that you have to use Chrome which bundled with the latest. There is also a hack to use up to date flash in Firefox (actually two).

---

### Post by dino99 on 2015-05-21
from a terminal:

[HTML]sudo dpkg -s <packagename> | grep 'Version'[/HTML]

(packagename for 'flash' can be 'flashplugin-installer' or 'pepperflashplugin-nonfree' (used with chromium-browser)

or from synaptic, you get directly the version, changelog, ....

---

### Post by oldos2er on 2015-05-21
Should be ```
dpkg -s flashplugin-installer | grep Version
``` No need for sudo and the single quote marks around Version just confuse bash.

---

### Post by ajgreeny on 2015-05-21
Or you can see which version Adobe says you've got at [Adobe - Flash Player]("http://www.adobe.com/uk/software/flash/about/")

That may be the info that you want or need rather than the package number which is different from the flash version of the pepperflashplugin-nonfree or the freshplayerplugin.

The use of a ppa "hack" to use pepperflash in Firefox is now working very well in 14.04 and later versions, using flash version 17.0.0.188 at the moment, the same as is available in Windows, or when using Google-Chrome or the pepperflashplugin-nonfree which is needed for flash in chromium.

To try it first remove whatever flash packages you have now then use commands ```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
```

You should now find that the [Adobe - Flash Player]("http://www.adobe.com/uk/software/flash/about/") site reports flash 17.0.0.188, like mine.

---

### Post by Dennis N on 2015-05-21
And Firefox will inform you of the version it is using at:

**Menu > Tools > Add-ons > Plugins**

or 

**Menu Button > Add-ons > Plugins**

---

### Post by ajgreeny on 2015-05-21
> **Dennis N said:**
> And Firefox will inform you of the version it is using at:

**Menu > Tools > Add-ons > Plugins**

or 

**Button > Add-ons > Plugins**Not quite.
My machine with thr pepperflashpluin and freshplayer plugin tells me I have flash version 13. but the adobe site tells me I.have 17.0.0.188.
 Go figure that!

---

### Post by Dennis N on 2015-05-22
> **ajgreeny said:**
> Not quite.
My machine with thr pepperflashpluin and freshplayer plugin tells me I have flash version 13. but the adobe site tells me I.have 17.0.0.188.
 Go figure that!

Mine shows the same in the Add-ons window and the adobe site - as it should. Both are 11.2.202.460 (as of May 22 '15)
I have no 'pepperflash' on the system.

---

### Post by monkeybrain20122 on 2015-05-22
Op didn't mention anything about pepperflash (or pipelight flash) so he meant good old flash 11.2. I don't think your commands would find anything else. :)

---

### Post by ajgreeny on 2015-05-22
> **monkeybrain20122 said:**
> Op didn't mention anything about pepperflash (or pipelight flash) so he meant good old flash 11.2. I don't think your commands would find anything else. :)

No indeed he didn't, but I was making those comments simply to add extra information for the OP as I find that the newer version of flash (the pepperflash plugin) is much smoother and better than the old 11.2 version from Adobe, and I did wonder if the query was a precursor to a problem that would follow; I was not intending to confuse.

My commands certainly do work on 14.04 to get flash version 17.0.0.188 to work in Firefox, though I can not vouch for any earlier versions of Ubuntu.

---

### Post by monkeybrain20122 on 2015-05-22
yes, the freshplayer-plugin seems to work very smoothly on Firefox, but still not working as well as it is in Chrome (hardware acc doesn't work probably due to FF's limitations and certain drm streams play in Chrome but not freshplayer-plugin, webcamb isn't recognised, but these are probably minor as flash 11.2 on Ff doesn't have hardware acceleration except maybe on Youtube if you set it up and drm stream wouldn't play anyway) I have never used it on Ubuntu though, I use it on Fedora on another partition but over there needs to compile from source and must install Chrome since there is no separate pepper-flash package.

---

