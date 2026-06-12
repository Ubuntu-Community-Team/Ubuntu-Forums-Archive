---
title: "Issues with display going blank when idle."
date: 2017-06-18
forum: General Help
---

### Post by Roasted on 2017-06-18
Hi friends. I've been having an issue with my 17.04 Ubuntu Gnome system. This was a brand new install of 17.04 about 2 months ago. Lately I've been having issues with the screen timeout acting strange. For some quicker tests I set my timeout to 1 minute. Nearly every time, the system will begin to fade the LCD until it goes blank, and after one full second, it snaps back to full brightness as if I struck a key or moved the cursor. Thing is, I'm not touching it in these cases.

I looked in dconf and set my timeout to some obscure delays to test. They too acted weird. As I mess with the timeout in system settings/power menu and then check dconf, dconf yields the setting I just selected in system settings. I'm not really understanding why Gnome isn't honoring these changes, or at least in most cases it tries to but then snaps back as if I canceled the screen timeout. Has anybody seen this?

---

