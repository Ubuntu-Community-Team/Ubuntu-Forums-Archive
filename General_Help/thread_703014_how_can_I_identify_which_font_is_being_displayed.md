---
title: "how can I identify which font is being displayed?"
date: 2008-02-20
forum: General Help
---

### Post by BattlePanic on 2008-02-20
I often find that when I'm browsing the web in Firefox, I want to know which of my installed fonts is being used to display a given web page.  The font is being displayed right in front of me, but I want to know what it's called.  Does firefox, or, perhaps even more generally, the X server provide a way to tell me this?

---

### Post by MobiusNZ on 2008-02-21
If you get the Firebug extension (google it), you can identify which font-family is being used. From there you can work out the font by finding the first font in the list that is installed on your system. 

Eg if the font-family is 'Arial, Helvetica, sans-serif', then the font will be Arial unless you don't have it, in which case it will be Helvetica unless you don't have it, and so on till you get to the last one, which is usually a specified default font. 

You can find your default fonts (which determine what sans-serif, serif, monospace, etc actually are) in your preferences.

---

