---
title: "gnome deskbar lost web search and beagle"
date: 2007-07-22
forum: General Help
---

### Post by Goliath! on 2007-07-22
I had this problem which I got solved with help from sebp on #deskbar on irc.gnome.org.  I'm posting it because I couldn't find an answer elsewhere.

I was typing something in the deskbar when it crashed on me and disappeared from my panel.  When I re-added it to the panel, the Web Search and Beagle were gone.

I uninstalled Beagle and re-installed it (through Synaptics) and Beagle returned to deskbar's list of loaded extensions.  However, I couldn't find a way to re-add the Web Searches.

Sebp told me to do this:

In a terminal execute /usr/lib/deskbar-applet/deskbar-applet -w.  Tracing through that output I could see a message that says "Firefox is not your preferred browser, not using it."

So I set my preferred browser to Firefox in System > Preferences > Preferred Applications.  I removed deskbar from my panel, re-added it, and my Web Searches was there.  Hooray!

Sebp says that the Web Searches are meant to be used only with Firefox.

---

