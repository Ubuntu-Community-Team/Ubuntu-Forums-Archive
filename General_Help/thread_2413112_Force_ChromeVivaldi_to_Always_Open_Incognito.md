---
title: "Force Chrome/Vivaldi to Always Open Incognito"
date: 2019-02-21
forum: General Help
---

### Post by Iggy64 on 2019-02-21
[SIZE=2]I run Firefox almost always in "private" mode, for a variety of reasons.  To ensure this, I have set the flag
[/SIZE][COLOR=#333333][FONT=Ubuntu][SIZE=2]
browser.privatebrowsing.autostart=TRUE. 

 Therefore, whenever FF opens -- whether via the launcher or via clicking a hyperlink -- it opens in private mode.

I would like to do the same thing with Chromium and/or Vivaldi.  Unfortunately, I can find no such flag in Chromium. 

 I can modify its launcher by adding "--incognito" to the executable, and the launcher now opens an incognito window.  But this is only helpful when using the launcher. 

 If Chromium is my default browser and I click a URL hyperlink or an HTML file, the launcher is not involved.  So Chromium opens in normal mode.

[/SIZE]Is there a way to make Chromium always open incognito, similar to Firefox's capability?


[/FONT][/COLOR]

---

### Post by dmnur on 2019-02-22
You could override the Chromium desktop file locally for your user by running:
```
mkdir -p ~/.local/share/applications
cp /usr/share/applications/chromium-browser.desktop ~/.local/share/applications/
```

Then open **~/.local/share/applications/chromium-browser.desktop** in a text editor, append **--incognito** to the **Exec** line and save.

Finally, run:
```
xdg-desktop-menu forceupdate
xdg-settings set default-web-browser chromium-browser.desktop
```

For Vivaldi it's the same procedure, just search for its desktop file in **/usr/share/applications**. And, of course, you can only have one default web browser, so run the last command only where it's needed.

---

