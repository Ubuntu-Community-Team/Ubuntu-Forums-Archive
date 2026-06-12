---
title: "Tracker not doing anything"
date: 2007-04-04
forum: General Help
---

### Post by CocoAUS on 2007-04-04
Beagle has been randomly spiking in resources usage (especially when my PC is idle for a while), so I switched to Tracker.

However, it doesn't appear Tracker is doing anything.  It tells me it's adding polls all the time, and that's about it.  I told it to index my entire filesystem ("/"), but yet when I type a word into the search tool, it doesn't do anything.  When I click the Find button, the window goes dark for a few moments (I'm using Beryl), and then comes back, still reading "No files found."

Am I missing something?  Has Tracker not indexed anything?  What's all this polling about?  Why is Tracker never doing anything?

---

### Post by geetarista on 2007-04-05
I'm having the same problem as well.  I've also tried to use the tips from their website:

[http://www.gnome.org/projects/tracker/start.html](http://www.gnome.org/projects/tracker/start.html)

Nothing there helped though.  I installed it from the universe repository in Feisty and it shows that it's installed, but that's about it.

---

### Post by CocoAUS on 2007-04-05
I, too, have been through the documentation.  I can watch it use resources sometimes, but other times the process just sleeps.  I hear good things about Tracker, and would love to use it, but if it simply doesn't work...then I simply can't use it!

---

### Post by geetarista on 2007-04-05
OK--thanks to Feisty's cool terminal suggestions, I've finally figured it out.  Just install these packages, and everything should work fine: libtrackerclient-dev tracker-utils tracker-search-tool

---

