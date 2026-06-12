---
title: "Firefox Menu Text Color"
date: 2006-12-02
forum: General Help
---

### Post by Ohmz on 2006-12-02
I seem to be having a bit of trouble getting my Firefox config to cooperate with me. I downloaded and installed a theme that changed most things to a blackish color, and the top menu bars of windows to a nice blue/green fade. It looks nice because most windows have white text over that background, but for some reason Firefox has black. It makes it impossible to read the menu choices, so I went about changing it to white.

I've poked around in /etc/Firefox/prefs, profile and chrome. The one way I managed to change it was by adding the string ui.menutext to about:config and setting the value to white. I closed the browser, opened it up and it was white text!! But of course after closing it and reopening it was back to black, and I haven't been able to change it again. If anyone can help that would be great, I know I sound really picky but it just starts to bug me. Thanks ahead of time!

---

### Post by igknighted on 2006-12-02
I had a similar issue... try edit->preferences->content->colors and then uncheck the box that says 'use system colors'.  You should then be able to set the text color to whatever you want.

---

### Post by Ohmz on 2006-12-02
The problem is that Firefox's settings are not classified under System Preferences, and it seems like the text color for the toolbar (not titlebar) is controlled by Firefox. I just need to find a permanent way of adding ui.menutext to settings.

---

