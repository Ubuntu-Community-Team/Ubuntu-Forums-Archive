---
title: "window decorations disappear after typing 'desktop'"
date: 2008-04-27
forum: General Help
---

### Post by m6ixty2wo on 2008-04-27
Hi, so I haven't used these forums that often. But I was wondering if any of you also experienced this problem.

When using Gutsy, my window decorations would randomly disappear, and then I couldn't exit out of those windows anymore. I just ended up killing whatever process had that window open, and restarting it. It was more annoying than anything.

Now, using Hardy, my window decorations disappear in a consistent fashion. Whenever I type the word "desktop" in any context in any window, the window decorations disappear. E.g. when I try to open a file in my terminal window by typing "vi desktop_settings.txt" or something like that, the window decoration around the terminal window disappears. Or when I search "desktop" in the search bar in firefox, the window decorations around the browser window disappears.

Am I the only one experiencing this? Because this seems like an easy problem to fix.

It might have something to do with Compiz? Since both Gutsy and Hardy use it, and I've never had these types of problems before Gutsy.

I'm using a dell d820 with a NVIDIA Quadro NVS 120M video card. Thanks

---

### Post by rubicon on 2008-04-27
Wow. What a wonder :P

It may be one of the compiz plugin (e.g. windowrules) which searches text **in** window instead of searching it in window's caption/class. Try disabling some plugins and localize roots of the problem! :)

---

