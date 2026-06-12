---
title: "What's up with Avant-Window-Navigator"
date: 2008-07-09
forum: General Help
---

### Post by Sealbhach on 2008-07-09
It acts only as a window switcher, not as a dock.

I enabled the repository and used the development version here:

[http://wiki.awn-project.org/DistributionGuides](http://wiki.awn-project.org/DistributionGuides)

but it still behaves only as a window switcher.

Las time I downloaded AWN, about a month ago or so, it worked fine.

Anybody know what's happening with it?

I've got cairo-dock but I really like the spotlights in AWN.

.

---

### Post by sayakb on 2008-07-09
What exactly do you mean by **Window Switcher**. Sorry, couldn't comprehend..
I would rather recommend you this: [http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml](http://news.softpedia.com/news/Install-AWN-on-Hardy-Heron-82611.shtml)

---

### Post by Sealbhach on 2008-07-09
When it starts up, there is a tiny sliver in the middle, which is the dock.

There are no icons on it. When I start up an app, the icon for it appears on the cock, but when I close down the app, I'm left with this miserable empty thin sliver of a dock...


.

---

### Post by sayakb on 2008-07-09
That is normal. The AWN you installed from the repos doesn't have any applets by default. Install AWN from the link I provided. Then after launching it, right click on it and click **Dock Properties** to launch AWN manager and add applets from the AWN Manager window.

---

### Post by Kprojekt on 2008-07-09
Seriously, all the information , Sources and dependencies are here.... however this is still test software, being made compatible with Hardy (what's so different??) 

[http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive](http://wiki.awn-project.org/DistributionGuides#Testing_Package_Archive)

So just add the following to etc/apt/sources.list:

deb [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/awn-testing/ubuntu](http://ppa.launchpad.net/awn-testing/ubuntu) intrepid main

Then install it...

sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr awn-manager-bzr

And if you want the functional applets.... (which you do!)

sudo apt-get install avant-window-navigator-bzr awn-manager-bzr

---

### Post by moonbeam on 2008-07-09
I'm expecting this is due to a recently committed change.

I'll be making a post on this in a bit... I'll link to it then.

For the moment I'd suggest going into awn-manager.

1) close awn.
2) Remove any the applets from the applet list then add them back.
3) start awn back up.

---

