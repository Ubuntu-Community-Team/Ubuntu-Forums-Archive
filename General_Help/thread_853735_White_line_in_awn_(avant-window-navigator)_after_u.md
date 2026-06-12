---
title: "White line in awn (avant-window-navigator) after upgrade"
date: 2008-07-08
forum: General Help
---

### Post by Ruazinn on 2008-07-08
Just upgraded avant-window-navigator.  Now there's an annoying white vertical line...  Anyone else seen this?  (See attached screenshot)

I did a distribution upgrade from gutsy to hardy over the weekend.  Then, this evening, I updated the source repository lines for awn.  Got an error when I tried to update awn, so I uninstalled all the old awn entries, then reinstalled avant-window-navigator-bzr and associated stuff.  All went well, except for the annoying white line.

The old sources.list lines, which the dist upgrade commented out, are:

# deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

The new lines I added are:

# New stuff added in order to update avant-window-navigator-bzr 7/8/2008
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

And this is the stuff I have installed:

avant-window-navigator-bzr, awn-core-applets-bzr, awn-manager-bzr, libawn0-bzr, and python-awn-bzr.

Thanks!!!

---

### Post by Ruazinn on 2008-07-08
Upon further fiddling around, I discovered the white line is caused by the trash applet.  Didn't particularly care for it anyway, so I removed it.  But why does the trash applet not work correctly?

---

### Post by isaacj87 on 2008-07-08
> **Ruazinn said:**
> Upon further fiddling around, I discovered the white line is caused by the trash applet.  Didn't particularly care for it anyway, so I removed it.  But why does the trash applet not work correctly?

I had the same problem today after an update...I merely removed the trash applet and added it again.

---

### Post by Truedream on 2008-07-08
You can check [here]("http://wiki.awn-project.org/FAQ#Why_does_my_bar_have_one_or_more_thin.2C_vertical.2C_white_lines_that_extend_beyond_the_dock.3F").

---

### Post by Ruazinn on 2008-07-09
Well, I removed all awn items (see screenshot 1), then all compiz items (see screenshot 2), then reinstalled them in the reverse order.  Now, when I open awn manager to look at the list of applets, only the Launcher/Taskmanager applet is available, and it's listed twice.

Where o' where did the applets go?  I installed awn-core-applets-bzr, as well as the other items from screenshot 1.

---

### Post by MidEvilHungarian on 2009-11-03
> **Ruazinn said:**
> Just upgraded avant-window-navigator.  Now there's an annoying white vertical line...  Anyone else seen this?  (See attached screenshot)

I did a distribution upgrade from gutsy to hardy over the weekend.  Then, this evening, I updated the source repository lines for awn.  Got an error when I tried to update awn, so I uninstalled all the old awn entries, then reinstalled avant-window-navigator-bzr and associated stuff.  All went well, except for the annoying white line.

The old sources.list lines, which the dist upgrade commented out, are:

# deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
# deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

The new lines I added are:

# New stuff added in order to update avant-window-navigator-bzr 7/8/2008
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) hardy main

And this is the stuff I have installed:

avant-window-navigator-bzr, awn-core-applets-bzr, awn-manager-bzr, libawn0-bzr, and python-awn-bzr.

Thanks!!!

Those white lines are apps that was there before and gone in the new (ubuntu 9.10)
version of AWN, if you go to the applet window you see there are some "gears" icon instead of the app icon, 
for me the "file browser" was gone and the old "clock applet" was gone, 
do what i did and remove those and replace them with a suitable substitute, there are plenty of them.

i hope this helps.

---

