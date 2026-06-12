---
title: "Running thunderbird as two different users in one X session"
date: 2005-10-16
forum: General Help
---

### Post by holomorph on 2005-10-16
I had my desktop set up in Hoary so that my sister and I could both run mozilla-thunderbird as our respective user in the same x session.  I did this by creating two shortcuts.  For example, when logged into my desktop I have one that just runs 'mozila-thunderbird', which obviously opens thunderbird as me.  I have a second shortcut that runs 'gksu -u alexis mozilla-thunderbird', which would open thunderbirnd as her, after prompting for her password.  In hoary we could both have our instance of thunderbird running.  I upgraded to Breezy, and now have some strang (undesired) behavior:

If no instance of Thunderbird is running, each of the above described shortcuts launch the expected instance of thunderbird (good).  Unfortunately, if one of us has already launched thunderbird, clicking on the other shortcut will just bring to the front the one that is already running (bad).  So we can run one, or the other, but not both at once.  Obviously we'd both like to have our mail open most of the time, since this machine is mostly just for mail and web activities.  

This does seem to be specific to thunderbird (maybe other apps too, but not all, I tested glxgears and gnomine, both will launch as multiple instances).

Anyone got any suggestions about how to get the previous behavior?  On the up side, it seems launching thunderbird multiple times as the same user does not result in being prompted to select a profile other than "default" which is already open anymore, I suspect the new behavior is related to fixing that bug.  

Bjorn

---

### Post by munkymonkjr on 2005-10-16
not a fix, but a temporary work around. 

create a new launcher on the desktop and for the command add "su alexis mozilla-thunderbird" and mark it to "launch in terminal". So when you click that icon a terminal will pop up asking for her password, once you type it in and press enter, her instance of thunderbird should launch.

---

### Post by holomorph on 2005-10-17
Regular 'su' won't work because it doesn't do the X authorization magic.  You end up with something like:
(mozilla-thunderbird-bin:9395): Gtk-WARNING **: cannot open display:

---

