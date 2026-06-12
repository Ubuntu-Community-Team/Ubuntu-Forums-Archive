---
title: "Catch-22 with Firefox 2 in Hardy"
date: 2008-04-30
forum: General Help
---

### Post by mb_webguy on 2008-04-30
I recently installed Hardy after having used Feisty for quite some time.  I don't want to use Firefox 3 as my browser until it gets out of Beta and my favorite extensions and themes are supported (of which less than a quarter currently are).  However, it seems that all of the Firefox plug-ins (and specifically, the mplayer plugin) have the Firefox 3 packages as dependencies.

I don't want to install Firefox 3, because it messes up my installation of Firefox 2.  But I can't install the Mozilla plug-ins from the repositories without installing Firefox 3.  I thought about compiling the mplayer plug-in from source, but it requires the gecko-sdk, which in turn requires compiling xulrunner (as the repository version doesn't seem to include the gecko-sdk as far as I can tell).  That seems to be quite a bit of hassle just to install a browser plugin...

This problem will, of course, resolve itself once FF3 is out of Beta for a while, but until then it's a bit frustrating for those of us who don't want to use pre-release software.  So... I guess would it be possible for someone to send me the mplayer plugin files for Firefox 2?

---

### Post by Nunu on 2008-04-30
+1 on that. And the fact that the firefox website only does the windows versions of the plugins doesn't help either *Sigh*

---

### Post by mb_webguy on 2008-04-30
Ok, problem solved.  It occurred to me that the desktop PC I'm using as a file server was running Gutsy and probably had FF2 and the mplayer plugin installed.  After checking, that turned out to be correct.  The plugin files seem to be the same as those in the Hardy repository, and after copying them over to my main PC I can now play embedded videos in FF2.  Yay!

So for anyone else who wants to keep FF2 as their browser but can't install the plugins because of the Firefox3 dependencies, I'm attaching the files for the mplayer plugin.  Just extract the archive to /usr/lib/firefox/plugins and you're all set.  Keep in mind that you do still need to install mplayer for the plugin to work!

---

