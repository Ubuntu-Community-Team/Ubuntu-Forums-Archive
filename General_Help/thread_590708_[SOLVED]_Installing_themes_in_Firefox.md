---
title: "[SOLVED] Installing themes in Firefox"
date: 2007-10-25
forum: General Help
---

### Post by Kappity on 2007-10-25
I've been trying to install a Firefox theme through the normal Firefox menu.  I go to "get themes", select the one I want, and click install.

Every single time I do this it takes a very long time, begins to download the theme, and then terminates with a "download error".  I've tried this with several different themes, and on three different days, in case it was just a temporary problem with the Firefox download site.

I'm using Ubuntu 7.10 with version 2.0.0.8 of Firefox.  It was probably a previous version of Firefox until today, when the automatic updates for Ubuntu included a Firefox update.  Has anybody else seen the same problem?  I've installed themes in Mac OS X before, and it seems like it's exactly the same procedure, so it should work.

---

### Post by alienexplorers on 2007-10-25
Try going into your profile and deleting your downloads.rdf file.
> [http://kb.mozillazine.org/Downloads.rdf](http://kb.mozillazine.org/Downloads.rdf)

---

### Post by Kappity on 2007-10-25
Turns out that the solution is described in [this thread]("http://ubuntuforums.org/showthread.php?t=587533&highlight=firefox&page=2"), concerning Firefox plugins generally.  I edited /etc/hosts/ as suggested, and was able to get the theme that I wanted.  Thanks vyvee from that thread.

---

