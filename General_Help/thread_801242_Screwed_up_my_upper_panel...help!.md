---
title: "Screwed up my upper panel...help!"
date: 2008-05-20
forum: General Help
---

### Post by dartmusic on 2008-05-20
Hi all...I'm running Hardy currently on my HTPC.  I tried using Compiz which looks great and runs without issue, except, of course, on an HTPC I'm having video issues, so I disabled it.  Before I disabled it I was using the AVN dock, so I had deleted the lower dock and took a lot out of the upper dock.  When I went back to a non-Compiz desktop and removed the AVN dock I had to replace come things in the upper panel.  Now I have notifications happening in the same place that the main Ubuntu menu is and I don't have the update manager icon (the orange burst) any longer.  I can't figure out how to get the upper panel back to the standard config.  Does anyone have any idea how to restore it to its former/original configuration?

Thanks!

---

### Post by perillux on 2008-05-20
well it's pretty simple to just move things around back to the way they were.
you can right click and lock or unlock them so you can move them, or even delete them.  If something is missing altogether you can right click anywhere on the panel and click Add to Panel and find what you need.

So say ur starting from scratch (the upper panel is blank, note: you can get it this way by simple right clicking and removing everything).  Or you can remove the entire panel and add a new one.
Right click and select Add, locate "Menu Bar" in the list and click add (that should go to the very left)
also add the following:
"Notification Area"
"Volume Applet"
"Clock"
"Quit..."  <do not quit, this means find the menu item "Quit..." and add it.  lol

Then close that window, and arrange the items so they look like this:
[http://toastytech.com/guis/ubuntu7desktop.png](http://toastytech.com/guis/ubuntu7desktop.png)
once you are satisfied right click and lock them all into place.

then all that's left is to add the 3 icons, right click>Add to panel highlight Custom application launcher and click add, enter the following info:
[i]Type: Application
Name: Firefox Web Browser
Command: firefox %u
Comment: Browse the World Wide Web[/i]
but before you close that window click the icon so you can set it to the firefox icon and type "/usr/share/pixmaps/firefox-3.0.png" into the box and click ok, then close the window.

Do the same thing again but enter this info:
[i]Type: Application
Name: Evolution Mail
Command: evolution --component=mail
Comment: Read and write emails[/i]
click the icon and enter this  "/usr/share/icons/Human/scalable/apps/evolution.svg"  click ok and close.
and your all set :)

I deleted my help icon so I can't give you all the info on that, but you should be able to come up with something if you really need it.
Then just lock those icons into place.



**IF THAT DOESN'T WORK** or solve your problem or answer your question for any reason then you can simply type this into a terminal:
**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**
That will reset all your gnome settings, you probably have to log in again after you do this, so hit *ctrl+alt+backspace*

hope that helps.

---

### Post by jimv on 2008-05-20
Just move your stuff back around.  Middle click on your mouse will move the icons around.  The update manager only shows up when there are updates, and that shows up in the Notification area applet, which you could add to the panel, and place just to the left of the time.

---

### Post by dartmusic on 2008-05-20
Thanks for the replies.  I understand how to add/delete/move items on the panel, but there are problems.  I can't select the notification area, but it pops up under the main menu.  I also can't find an applet for the update manager notification icon, just to add a shortcut TO the update manager.  Hopefully this makes sense.

I don't really want to reset all gnome settings, so hopefully someone has more info?

Thanks again!

---

### Post by jimv on 2008-05-20
OK, I don't know if there is a way to just reset the panels, so I think if we just set one up from scratch you should be ok.

Right click on your current top panel and click New Panel.  A new panel should pop up (probably on the right or bottom).  Once you have the new panel, right click on your top panel and click Delete This Panel.

Then, just click and drag the new panel to the top of the screen.  It should automatically flip up there.  Then add these applets:

Menubar, Notification Area, Network Monitor, Volume Control, Clock, Quit

As far as I know, there isn't an Update Manager applet, but if you go to System > Preferences > Sessions > Startup Programs, there should be an option for Update Notifier checked.  If it isn't there, open a terminal and type:

```
sudo apt-get install update-notifier
```

---

### Post by dartmusic on 2008-05-20
That last response was perfect...thanks!

---

