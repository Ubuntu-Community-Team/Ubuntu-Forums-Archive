---
title: "Ubuntu 17.10 - CompizConfig not working"
date: 2017-10-21
forum: General Help
---

### Post by qorka on 2017-10-21
I'm having trouble setting up my windows to remember their positions - for example, i'm trying to get Adobe Brackets to open maximized and terminal to open at certain X, Y coordinates. CompizConfig isn't acknowledging anything I enter. Any idea why that is? Was there a change in the update?

---

### Post by drs305 on 2017-10-21
I am having CCSM issues with window decorations and keybindings (especially xmacro assignments). I suspect the issue is the 17.10 update and/or Wayland integration with CCSM.

If you are running GNOME/Wayland you could try logging in via X to see if the problem persists. You can choose at login by clicking the Settings cog. If you don't see it, click to sign in as another user, type in your normal username, and then on the next screen the cog should appear.

---

### Post by mc4man on 2017-10-21
> **qorka said:**
> I'm having trouble setting up my windows to remember their positions - for example, i'm trying to get Adobe Brackets to open maximized and terminal to open at certain X, Y coordinates. CompizConfig isn't acknowledging anything I enter. Any idea why that is? Was there a change in the update?
What are you running?
Ubuntu 17.10 does not use compiz so anything set in ccsm will be useless.

---

### Post by qorka on 2017-10-21
That would explain it then - (i'm an ubuntu newb) ~ any suggestions on setting defaults for windows placements? ie: opening Brackets maximized

---

### Post by dragonfly41 on 2017-10-21
I opened my Brackets on Ubuntu 16.04 and I could not find a maximize command, or configuration which is odd (although there is an extension I found).

Instead you can just hit [Super_key]+[arrowup_key] to maximize and [Super_key]+[arrowdown_key] to toggle back.

[later edit]

By coincidence, I am right now in the process of automating windows placements for a workflow and for the terminal placement I use .. as example ..
```
gnome-terminal --geometry 73x31+100+300
```

For other placements I use the automation utility Actiona you find in Accessories.  For example position terminal in focus over a launched web page and handshake between them.

---

### Post by mc4man on 2017-10-21
I don't think it's a preference based on
[https://github.com/adobe/brackets/wiki/How-to-Use-Brackets#preferences](https://github.com/adobe/brackets/wiki/How-to-Use-Brackets#preferences)

The window info shows a min. size reported (Program supplied minimum size: 354 by 23) so possibly the default size is set in source.
Best bet would be to do as post above
(- or use 16.04.3 instead of 17.10..

---

