---
title: "Browser as Xscreensaver Weirdness"
date: 2013-08-07
forum: General Help
---

### Post by eosha on 2013-08-07
My goal is to have my Google Calendar appear as a screensaver. As such, I sudo edited my .xscreensaver to add 
```

programs:                                      \
                chromium-browser --app calendar.google.com  \n\
```

Now when I go to my xscreensaver control panel, Chromium-browser appears as an option. Choosing that option in the list opens the calendar full screen (as opposed to in the little preview window). 

However, when I choose the menu option "Blank Screen Now", or click the "Preview" button, or wait for the normal time delay, the screen fades to black as normal and then doesn't display anything further. When I then go into the File menu, all the daemon options besides "Restart Daemon" have gone grey, indicating to me that the daemon has crashed.

Edit: I also added ```
opera --kioskmode calendar.google.com
``` to the .xscreensaver and got exactly the same behavior.

---

