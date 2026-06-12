---
title: "Chrome Java plugin won't load (Ubuntu 14.04 LTS)"
date: 2014-05-30
forum: General Help
---

### Post by Lorin Ricker on 2014-05-30
Sorry, I hate to open this topic again, as there's been a lot of traffic here at Ubuntu Forums and elsewhere on the 'net, but all that stuff is pretty old, prior to 2012.  I've got several 14.04 "Trusty" systems, desktops and a hot new S76 laptop, all show this same problem:

Problem is that I can't get the **Chrome** browser (Version 34.0.1847.116 Ubuntu 14.04 aura (260972)) to recognize and load, much less "enable", the Java plugin.  However, **Firefox** loads/enables it fine.

Currently, **Chrome** loads and enables these two plugins: [COLOR=#000000][FONT=Arial]**Adobe Flash Player**[/FONT][/COLOR][COLOR=#000000][FONT=Arial]- Version: 13.0.0.206, and [/FONT][/COLOR][COLOR=#000000][FONT=Arial][B]Chromoting Viewer.

[/B][/FONT][/COLOR]**Firefox** shows seven plugins: Shockwave Flash 11.2r202, iTunes Application Detector, **IcedTea-Web Plugin (using IcedTea-Web 1.5 (1.5-1ubuntu1))**, QuickTime Plug-in 7.6.6, DivX Web Player, VLC Multimedia Plugin (compatible Videos 3.10.1), and Windows Media Player Plug-in 10 (compatible; Videos).
So, obviously **Firefox** sees, loads and enables the Java plugin (IcedTea), but **Chrome** cannot.  I've gone to the (futile) extent of completely removing both the **icedtea-7-plugin** and the **openjdk-7-jre **packages (using $ sudo apt-get purge...) and then reinstalling both.  No Joy.

Old conversations & advice from this Forum and elsewhere (google: "chrome java plugin install ubuntu") give the advice to create a sym-links in each one of several directories, e.g., **~/.mozilla/plugins/**, **/usr/lib/chromium-browser/plugins/**, and even **/opt/google/chrome/plugins/** ...  The sym-links suggested are:

  **./libnpjp2.so -> /usr/lib/jvm/java-1.7.0-openjdk-amd64/jre/lib/amd64/libnpjp2.so**
and
 **./IcedTeaPlugin.so -> /usr/lib/jvm/java-1.7.0-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so**


I've tried each of these in turn, with again No Joy.  Heck, the file **libnpjp2.so **doesn't even seem to exist in icedtea-7-plugin, but the file **IcedTeaPlugin.so** does...

I need more, better informed input and advice on this, as those old conversations seem to be just guessing.  Does anyone have any real advice on **Chrome** and how to get it to load and enable this Java plugin?  TIA!!!

Or is **Chrome** just seriously broken as to plugins, and the Google dev-team just doesn't care anymore?

---

### Post by Lorin Ricker on 2014-06-02
*Ok, I missed some things in my hasty research on this problem last week, but I dug in over the weekend and found all this stuff (hope it saves someone else some time wasted in digging into the details):*

This is a *Known Issue*, discussed and analyzed (if not "resolved") in two other threads this Forum:[ http://ubuntuforums.org/showthread.php?t=2225581]("http://ubuntuforums.org/showthread.php?t=2225581") and [http://ubuntuforums.org/showthread.php?t=2225273](http://ubuntuforums.org/showthread.php?t=2225273).  It is _not_ an Ubuntu 14.04 issue; it's a "new improved security feature" (which creates problems) released with **Chrome v.35 (Aura)**, released in early 2014.
 
Here's the bottom line, followed by some of the details --

For **Chrome v.35 (Aura)** forward, if/until the Google Chrome dev-team and/or the Oracle Java Plugin dev-team decide to develop and support a new PPAPI-based Java plugin, the user community's only recourse is to_** use Firefox**_** for any and all online applications and/or web-access which requires that Java plugin**.

Latest release(s) of Chrome (Chromium) have ceased to support the Java plugin (IcedTea) -- this is due to a totally justifiable decision to improve this browser's resistance to the innumerable security flaws and exploits which present from the Internet. Even so, apparently the Google Chrome development team did not fully appreciate the impact that this design decision would have on its user base... Although they accounted for ongoing access to Flash content (with a new-technology kind of plugin for Flash) so that we could all continue to watch cute-kitty videos, they totally failed to take into account the numerous user-base business and private reasons which *_require_* the Java plugin (e.g., many, many applications world-wide in banking, finance, medical, remote systems support, Citrix, etc.).  This Security Decision on Google's part leaves an indeterminate number of Chrome/Chromium users without recourse other than to switch browsers (back) to Firefox for online applications and access which requires the Java &/or IcedTea plugin.

Here are the (TL;DR) _details_, if you care to wade through it all:

First of all, this has all the earmarks of being a software dev-team, big-corporation *vs*. big-corporation (e.g., Google *vs*. Oracle; what, you thought that only MS did this?) techno-war, with the user-base (us folks) being caught in the middle, and then left out in the cold, as usual.  That this might be a  "techno-war" is a personal assessment of what I've read (see below); your mileage may vary...

The Chrome dev-team's original (?) announcement about the then-pending change is here: "[The road to safer, more stable, and flashier Flash - Wednesday, August 08, 2012]("http://blog.chromium.org/2012/08/the-road-to-safer-more-stable-and.html")".  Actually, their reasons for making this change from NPAPI to PPAPI make sense; it's just that their implementation and follow-through sucks and causes grief to their user community.  The announcement was perhaps even slightly mis-understood early in 2014 here: "[Use Chromium on Linux? Adobe Flash Will Stop Working From April - January 2014]("http://www.omgubuntu.co.uk/2014/01/chromium-npapi-flash-dropped-april-2014")".

Post/response #3 in Thread [2225581]("http://ubuntuforums.org/showthread.php?t=2225581") above provides two additional links to dev-team threads which converse and argue (at length) about this change to Chrome:  [https://code.google.com/p/chromium/issues/detail?id=375909]("http://code.google.com/p/chromium/issues/detail?id=375909") and [https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/xEbgvWE7wMk](https://groups.google.com/a/chromium.org/forum/#!topic/chromium-dev/xEbgvWE7wMk) -- If you plow through both of these, you can kind'a trace the thread of logic, why the Chrome dev-team decided to make this change (see also below), and how incompletely the impact of this change was thought through -- It's not until more than 1/3rd of the way down the dev-team's discussion thread that somebody, a user, finally says "Also Java!" ...Like the dev-team didn't even think of this critical plugin!

The announcement and rationale for this change is discussed in [this Wikipedia article about NPAPI]("http://en.wikipedia.org/wiki/NPAPI"): "Google announced later in 2013 that their browser will not support NPAPI plugins anymore, and will block plugins which use this technology. This includes Oracle's Java and Microsoft's Silverlight plugins, although these will be whitelisted during [the first] 5 months [of 2014]", and is justified further on in that same article: "Google Chrome / Chromium: In September 2013, Google announced that NPAPI support in Chrome would be phased out during 2014 because 'NPAPI&#8217;s 90s-era architecture has become a leading cause of hangs, crashes, security incidents, and code complexity.'"  Even more background about changes to Chrome's plugin support is given in the [Wikipedia article on Chrome]("http://en.wikipedia.org/wiki/Google_Chrome#Plugins") itself, with more here:  [NPAPI]("http://en.wikipedia.org/wiki/NPAPI") and [PPAPI]("http://en.wikipedia.org/wiki/PPAPI") (also known as "Pepper").

---

### Post by aedwards on 2014-06-04
Does anyone have any thoughts if Oracle will build a PPAPI layer?

---

### Post by david310 on 2014-11-10
Any news on this matter?

I've installed Icedtea Java Plugin and it's working well on Firefox. However, it doesn't work on Chrome current version.

According to Icetea official wiki page ([http://icedtea.classpath.org/wiki/IcedTea-Web](http://icedtea.classpath.org/wiki/IcedTea-Web)), the plugin is installed inside "/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64", with the name "IcedTeaPlugin.so".
The symlink that's supposed to work for both Firefox and Chrome is located in "/usr/lib/mozilla/plugins", with the name "libjavaplugin.so". This symlink points to "/etc/alternatives/mozilla-javaplugin.so", which points to "/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/amd64/IcedTeaPlugin.so".

With the symlink in the mozilla plugins under /usr/lib directory, Firefox is able to load OpenJDK7 perfectly, while Chrome doesn't even list it in it's extension configuration page.

Is that it? So Chrome doesn't have support for Java in Linux currently?

---

### Post by Lorin Ricker on 2014-11-10
As far as I've been able to discover (which isn't much more than inference), you've got it right, David -- "...Chrome doesn't have support for Java in Linux currently" (no question-mark, just a period).  And AFAICR, your summary is accurate as to plugins and symlinks.  Of course, Google doesn't believe that it has, or owes anything to (including information), "customers".  Apparently, we're all just clicks and personal information to acquire, hoard and sell... er, "monetize."  I seriously doubt that we'll hear anything responsible, informative or helpful from Google.  Yup, I'm forced to use Firefox (not a bad option) for OpenJDK7 sites too.  Short of "everybody in the world" switching permanently from google.com to duckduckgo.com (itself not a bad idea), I've got no clue how its user/"customer" base can influence Google in any productive way.

---

### Post by david310 on 2014-11-10
> **Lorin Ricker said:**
> As far as I've been able to discover (which isn't much more than inference), you've got it right, David -- "...Chrome doesn't have support for Java in Linux currently" (no question-mark, just a period).  And AFAICR, your summary is accurate as to plugins and symlinks.  Of course, Google doesn't believe that it has, or owes anything to (including information), "customers".  Apparently, we're all just clicks and personal information to acquire, hoard and sell... er, "monetize."  I seriously doubt that we'll hear anything responsible, informative or helpful from Google.  Yup, I'm forced to use Firefox (not a bad option) for OpenJDK7 sites too.  Short of "everybody in the world" switching permanently from google.com to duckduckgo.com (itself not a bad idea), I've got no clue how its user/"customer" base can influence Google in any productive way.

Thank you for your reply.

That's what I've imagined.

---

