---
title: "firefox icon in top left hand corner (when it's open) is blank. how can i change this"
date: 2007-05-01
forum: General Help
---

### Post by syxbit on 2007-05-01
the main icon works, but when i have a window open, the icon for firefox in the top left corner is blank.
where can i change this?
thanks

---

### Post by amohanty on 2007-05-01
It depends on the window border you are using (assuming you have ubuntu not kubuntu or xubuntu)

System->Preferences->Themes->Theme Details ->Window Borders.

If you are using the default theme, try launching FF in safe mode using
**firefox -safe-mode**

AM

---

### Post by strabes on 2007-05-01
The location for the icon in the title bar is /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm

For more info check this page: [http://www.ubuntux.org/how-to-replace-the-standard-browser-logo-with-the-firefox-logo](http://www.ubuntux.org/how-to-replace-the-standard-browser-logo-with-the-firefox-logo)

---

### Post by syxbit on 2007-05-01
i followed that guide, but my problem is because I used the mozilla repos to install thunderbird 2.0. by using these repos it also updates my firefox 2.0 to the mozilla build.
the firefox works fine, but the icon in the top left is gone.

the guide says to copy the icons to /usr/lib/mozilla-firefox
but i don't have such a DIR.
i created it, and moved the stuff there, but it didn't work
any ideas?

---

