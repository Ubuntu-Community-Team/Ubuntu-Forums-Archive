---
title: "Moving mouse between two external monitors"
date: 2022-03-18
forum: General Help
---

### Post by goemonburo on 2022-03-18
Hi, I have two systems both running Lubuntu 20.04LTS, both with twin external monitors that are arranged 1-2, extending the screen (not duplicating).  On my desktop, there's no "stickiness" when I move the mouse across from one monitor to the other, it glides smoothly and the moment it reaches the right edge of Monitor 1 it appears at the leftmost edge of Monitor 2.  This is how I want it.

On my laptop, however, the mouse gets "sticky" at the edge of the screen and to get it to cross the border between the two screens I have to redo it, almost like I'm getting a "running start," and go faster across...it will switch, but not smoothly.  

How can I fix this?  I don't know where to begin, whether it's in the display settings or something in the preferences of LXQt.  

Thank you!

---

### Post by #&amp;thj^% on 2022-03-18
This seems to be the "Sticky edges" which are activated in Ubuntu by default. Go to the System Settings, choose Screen Display and deactivate "Sticky edges".
see screenshot
Lubuntu I just saw, see if the code below works.
Or use in the terminal:
```
gsettings set org.gnome.shell.overrides edge-tiling false
```
to revert back use:
```
gsettings set org.gnome.shell.overrides edge-tiling true
```
I missed this:  Lubuntu 20.04LTS,

---

### Post by guiverc on 2022-03-18
I would likely compare the settings between your two machines..  

ie. ~/.config/lxqt/lxqt-config-monitor.conf

How the system interacts can be influenced by how you join them & setting settings like "*Keep monitors attached*"

Note:   sorry I don't use *focal* (or 20.04), and whilst I booted up a 20.04 box to check my reply; I didn't consider that it only has a single screen when I chose it, thus it has none of the options offered that are useful/needed in this response

If you don't like command line exploration; I'd check out the [WM (*window manager*) settings]("https://manual.lubuntu.me/lts/3/3.2/3.2.11/openbox_settings.html") etc, but sorry I can't recall where it's set, nor if it's an *easy-to-click* option on the LXQt version used in Lubuntu 20.04 LTS.

---

### Post by goemonburo on 2022-03-18
Thank you all for the help. I went back and looked closely and did not find any org.gnome.shell.overrides, BUT in the checking, I noticed that there was just a tiny bit of space between the two monitors in the Monitors setting.  So I nudged them closer together and that fixed it.  I'm so happy to have that all set.  Again, thank you!!!

---

### Post by guiverc on 2022-03-18
Glad you got it solved.

And **yeah**, as I'm involved with Quality Assurance for Lubuntu - I've experienced that issue (plus *overlaps* of the two monitors) what feels like *hundreds* of times, especially on older releases like Lubuntu 20.04 LTS.

I learnt to *drop* the second display slightly apart (if "*Keep monitors attached*" was enabled) to avoid such issues, esp. on 20.04 as the Qt5 LTS version used by 20.04 has a couple of strange issues (*that were fixed in later Qt5 versions used in later releases*).

I thought about mentioning that issue, but *quirks* like that from one release to another get forgotten over time, and for *focal* or 20.04 I need to recall back to late-2019 & early-2020 (ie. *prior to release of Lubuntu 20.04 LTS in 2020-April*) which was too long now to reliably recall (*thus why I didn't mention it*).

I'll suggest marking the thread as solved with your reply.

---

### Post by thomas1029 on 2022-10-25
Use the shortcut key to access the control panel right away after turning on your computer. Hit both the window and X keys. Using the [Mouse  Between Two Monitors]("http://monitormega.com/how-to-move-mouse-between-two-monitors/") You'll be directed to the control panel.
Select "Appearance and Personalization" from the menu. There will be the choice of resolution or resolution adjustment. Your monitors will be displayed as numbered icons. Select your displays by clicking on the numbered icon.
Drag the monitors now and arrange them next to one another as you did with your physical set-up. Your setting will be modified after you click OK.

---

