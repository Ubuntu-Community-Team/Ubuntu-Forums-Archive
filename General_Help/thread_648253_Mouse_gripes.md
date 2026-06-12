---
title: "Mouse gripes"
date: 2007-12-23
forum: General Help
---

### Post by Ryoushi19 on 2007-12-23
Mouse support on Ubuntu can get to be a pain sometimes.  Not to degrade the OS, or anything.  I like Ubuntu, but these flukes need to be fixed.  Firstly, when I press the middle mouse button on a webpage, it goes to another webpage, seemingly at random.  Why?  Why on earth would I want to go to some random webpage?  Why can't I use that button to scroll with a speed based on my distance from the origin point at which I pressed the button, like I'm used to?  And what happened to the back and forward buttons?  They don't even do anything on Ubuntu.  I want this to be fixed, and I want the fix to use stable drivers, aka not evdev.

---

### Post by jimrz on 2007-12-23
> **Ryoushi19 said:**
> Mouse support on Ubuntu can get to be a pain sometimes.  Not to degrade the OS, or anything.  I like Ubuntu, but these flukes need to be fixed.  Firstly, when I press the middle mouse button on a webpage, it goes to another webpage, seemingly at random.  Why?  Why on earth would I want to go to some random webpage?  Why can't I use that button to scroll with a speed based on my distance from the origin point at which I pressed the button, like I'm used to?  And what happened to the back and forward buttons?  They don't even do anything on Ubuntu.  I want this to be fixed, and I want the fix to use stable drivers, aka not evdev.

What type mouse are you using and which browser?

mouse: You will need to edit your /etc/X11/xorg.conf to get the side buttons working. I use intellimouse with scroll wheel + 2 side buttons, if yours is the same I can post the appropriate section here for you. Otherwise, post the type you have and also search these forums for the correct settings.

browser: If firefox, type "about:config" in the url bar, the filter on "middle" to manually adjust. You could also install the "Tab Mix Plus" extention and adjust your mouse/tab behavior manually.

---

