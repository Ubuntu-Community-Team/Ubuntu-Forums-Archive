---
title: "Firefox upgrade to 1.0.7"
date: 2005-09-21
forum: General Help
---

### Post by reuben on 2005-09-21
When will the security upgrade to 1.0.7 be available on the ubuntu repositories?

[http://www.frsirt.com/english/advisories/2005/1794](http://www.frsirt.com/english/advisories/2005/1794)

My company is requiring all linux desktops to upgrade ASAP, or risk being kicked off the network.

---

### Post by gat on 2005-09-21
I'm eager to see this too.  So far only 1.0.6 shows up in my repositories.  

Apparently it's a nasty URL-parsing problem that lets people inject shell commands via evil links.

At [http://www.mozilla.org/](http://www.mozilla.org/) they have a download link -- it unzips and untars into an installer.  I'm going to try it, but I can't tell if it's compatible.  I'll come back later and post the outcome.

---

### Post by gat on 2005-09-21
Well, it worked... as far as I can tell.

I pulled the package down from mozilla.org.  Once I unpacked it into a temp directory, I found a "firefox-installer" executeable script.  

I opened a terminal, went to that directory and typed "./firefox-installer".  A gui installer launched.  I used to create another folder within my /home directory and chose that as the install location (not sure if that was a bright idea, but I didn't want to try to overwrite my existing browser).

The gui installer ran fine, and, when it closed, popped up a firefox 1.0.7 window (I'm writing this in 1.0.7).  When it closed out, I noticed a few things...

I got some "pango" and "utf-8" warnings in the installation terminal, but they didn't seem to be very serious.

Synaptic has no idea that the new firefox is installed (and in fact, my old firefox is still running happily).

My old bookmarks, etc. actually showed up in the new firefox, but (of course) my old links, shortcuts, and menu items all still point to the old version (I have to launch the new one by clicking on the "firefox" icon in the install directory I built).

I'm planning to abandon this version as soon as I can get a more "official" version from the ubuntu repositories.

I hope that helps.

---

