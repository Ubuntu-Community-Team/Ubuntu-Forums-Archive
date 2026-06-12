---
title: "Automatically log off idle user?"
date: 2013-05-29
forum: General Help
---

### Post by zsld0423 on 2013-05-29
I guess I should preface this with a little info. This machine is just used as a kiosk, that automatically logs into a guest account when it starts. After that, it loads up Chromium only to a specific page (used for clocking in and out). I'm not sure how to go about setting it up to automatically log off after an idle period, such as 5 minutes. I've looked into using TMOUT, but that doesn't work, and neither do autolog or timeoutd. Every other forum I've seen either lists those 3 as a "solution" or go un-answered. Since this is only used for clocking in/out, there's no data that would need to be saved or worried about losing. I don't want it to just lock with a screensaver, in case a previous user was already logged on the website with their account. I haven't been able to find any other program that could do this, would anyone have any suggestions?

Thanks for any assistance!

---

### Post by ohnonot on 2013-05-29
maybe "if cpu-usage is below a certain threshold for x min, log out"?
this should be fairly simple to achieve with a shellscript that loops endlessly in the background. cpu usage could be queried with top or ps.
also, you could try to query the screensaver or power manager, and if it changes its state, logout.
some terminal-using will most probably be involved, how easy are you with that? reading man pages? you could start with "man xset" and "xset q". all these old and highly useful utilities from the early days are still there on every linux (graphical) install.

---

### Post by zsld0423 on 2013-06-12
duplicate

---

### Post by zsld0423 on 2013-06-12
Hey, thanks for the assistance :D I eventually figured it out, and wanted to put my solution on here because all the different searches I've done haven't yielded any working results for me. Your idea got me thinking about using the screensaver to log it out.


1. Download Xscreensaver (apt-get install xscreensaver)
2. Uninstall the Gnome Screensaver (apt-get remove gnome-screensaver)
3. Open up Xscreensaver and pick any screensaver, like Abscractile, and then Settings
4. Click "Advanced>>" to get to another section with a command line to run when the screensaver starts


P.S. Since this is a Kiosk, there's no Gnome shell loaded, so you can't use "gnome-session-save --force-logout" that just brings up an error because there's no Gnome shell loaded


5. Instead, what you can type is "kill -9 -1" This will logoff the Guest account and take it back to the login screen, where the next person can come up without interfering with the information of whoever was on last. 


Of course you'll need to be in the Guest account to do these changes, otherwise it'll do this to whatever account you're on now.
And just to have it on here, here's the script for the Kiosk to load Chromium only and open it back up if it gets closed


#!/bin/bash
xscreensaver -nosplash &
while true; do chromium-browser --start-maximized %u --incognito --kiosk; sleep 5s; done




Then just save that as a chromeKiosk.sh and put it in the /usr/share/xsessions folder, and set it as an executable.

---

### Post by ohnonot on 2013-06-12
linux is so cool hooray!

can you mark this as solved please, others will benefit!
(edit first post, go advanced, change title prefix)

---

