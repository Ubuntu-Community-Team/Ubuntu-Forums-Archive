---
title: "Mouse Click Suddenly Stops Working"
date: 2020-11-14
forum: General Help
---

### Post by sizzlefist2 on 2020-11-14
I had an issue a few months back after updating Ubuntu (with the update tool that opens automatically when new updates are available) where my mouse clicks would suddenly stop working after leaving my laptop idle for 5 mins.  I remember I read a post somewhere and solved it by reinstalling something like xinput?

Well now I updated Ubuntu again (I really regret it every time) and now the problem is back and I've been searching for hours and cannot find the solution.

Problem: After leaving the laptop idle for 5 mins (exactly) the UI becomes unresponsive to mouse clicks.  Everything in the UI seems to work fine it's not frozen.  The clock updates and any blinking lights on UIs that are visible continue to blink.  But nothing highlights on hover the left and right mouse buttons don't work.  A few mins ago I left the computer idle with my mouse hovering over a desktop icon.  There was a popup (tooltip?) with details of the desktop icon and after exactly 5 mins the tooltip disappeared and exactly then the mouse clicks went unresponsive.

I've tried turning off all power save settings.  Everything (sleep after; screen blank after; etc) is set to "Never".  Same issue.

I've tried reinstalling Nvidia drivers and going back to Noveau drivers.  Back to Nvidia drivers.  Back again.  Same issue.

On a side note ctrl+alt+F* does not bring up a console.  It's just a black screen.  Ctrl+alt+F7 goes back to the GUI but of course it's still frozen.

I wish I could remember how I solved it last time.  It was something like force reinstalling xinput or something like that.

Any help?  Please?  I've just hit a dead end here.

---

### Post by sizzlefist2 on 2020-11-14
Sorry forgot to mention I updated to Ubuntu 20.04 (and anything else that was suggested) and running Alienware 17 R4 laptop.

Prior to this I had a minor issue where when I opened the laptop (I guess from sleep) I would see the login screen for a second then it would go to the desktop.  All UI was updating just like it is with the current issue; UI would update; youtube videos would play and I could see them; lights would blink; etc; but mouse clicks ignored.  But if I did NOTHING but blindly type my password and hit enter suddenly I got back control.  I don't know if it's related.  Because I could leave the laptop open and running for days on end and it would work fine when I got back to it and moved the mouse and clicked on things.  Current issue is way worse.

Anyway any help appreciated.  Thanks!

---

### Post by sizzlefist2 on 2020-11-15
Just noticed something else strange.  If I have a youtube video playing the issue doesn't occur.  I can leave it for 5+ mins without losing the mouse.

I have screensaver; power settings; and lock screen all turned off everywhere I can find the options.  I checked the log files in /var/log and haven't come up with anything (not even sure what to look for anyway).  Last logs are just for the restart I had to force with Ctrl+Alt+PrtScrn C I R S U B

I've had issues like this for 2+ years.  Doesn't seem worth the frustration anymore.  I'm thinking Alienware R4 laptops are just not compatible with Ubuntu.

---

