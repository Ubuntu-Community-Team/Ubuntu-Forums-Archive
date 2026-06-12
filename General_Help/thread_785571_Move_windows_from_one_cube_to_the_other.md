---
title: "Move windows from one cube to the other?"
date: 2008-05-07
forum: General Help
---

### Post by 01000111 on 2008-05-07
I finally have Compiz running on my dual-head system with one cube on each monitor.  All's well, but I haven't been able to figure out how to drag a window from one monitor to the other.  If I simply try to drag the window, it takes me to other cube faces on the same monitor.

Little help?

01000111

---

### Post by iwallet on 2008-05-07
did you try "super+e" ?!

---

### Post by 01000111 on 2008-05-07
> **iwallet said:**
> did you try "super+e" ?!

Just tried.  Doesn't seem to do anything.  What plugin and action should that trigger?  Do I click and drag the window while holding super+e down?

Sorry for the basic questions...  I'm a Compiz noob.  :)

Also, since installing Compiz, it takes about a second or so for the hidden xfce panel to appear, and the same amount of time for menus to appear.  Is this a compiz or emerald setting?

01000111

---

### Post by myturntohide on 2008-05-07
Your cubes do what mine used to, you need to apply a bind key to moving between cubes so when you hold it down at the same time as dragging the window. The alternative is to use the Desktop Pane or Wall plug in (I will check on the actual name when I get home) and use the above Super+e combo, it will display all your desktop cubes unwrapped as 2 rows of 4 desktops, just drag the window from top to bottom or vice versa to get it from one cube to the other.

Hope this helps.

Tom

---

### Post by 01000111 on 2008-05-07
Thanks for the hints, but still no luck.  I don't see anywhere to setup a binding for moving windows across cubes.

As for my dropdown menus and panel delays, I've changed the effect to "none" for all of the menu-related effects, and have even tried turning animations off completely, and it still takes about 1 - 1.5 seconds for menus and the xfce panel to appear on my primary screen.  Strangely enough, on my secondary screen, menus appear instantly.

Also, I've found that if I run ccsm on each screen, I can set some effects to have different properties on each monitor.  I've tried, but haven't found a way to set cube rotate to different key bindings.  I'l love to be able to rotate one cube with ctrl-alt-left and the other cube with ctrl-super-left.

I seem to be asking a lot of questions.  Perhaps I should start different threads with the different queries?

01000111

---

### Post by iwallet on 2008-05-07
super+e should enable the "wall" of all your workspaces, and you can drag the windows on different workspaces... im not sure how it would work with a dual monitor... give it a shot.. you might have to enable it in ccsm

---

### Post by smartboyathome on 2008-05-07
Enable Expo in Advanced Desktop Effects (ccsm), and super-e should work.

---

### Post by 01000111 on 2008-05-07
Well, Expo enabled makes Super-e work, but I only see the cube sides (viewports?) of the cube on the monitor on which the pointer was positioned when I hit super-e.  I can move windows across the viewports, but not from one monitor to the other or one cube to the other.

Ug!

01000111

---

### Post by myturntohide on 2008-05-07
AHA there is a setting for that, its called Multiple Outputs, there should be something to do with that for either the cube and/or the Expo wall, this enables you to select one output, or seperate each monitor as different instances of the plugin. Try looking for that.

---

### Post by 01000111 on 2008-05-07
Thanks for all the help.  I tried all of the suggestions, but then, as an expirement, I changed the number of virtual desktops to 1 and turned off cube, cube rotate and cube reflections and still could not drag windows from one screen to the other.  THen I disabled compiz and went back to xfce4... still no luck dragging from one monitor to the other, so I figured the problem must be in xorg.conf.

I then re-ran nvidia-settings and re-enabled twinview, restarted compiz, and PRESTO!!!  I can drag from one cube to the other.  THis also fixed my slow menu problem as a bonus.

Interesting though, without twinview, i could manipulate the two cubes seperately, with twinview, the rotate command moves both cubes at the same time... not sure which I like better... maybe an option for a future compiz version.

Thanks again for all the help.

01000111

(that's a binary "G" in ASCII for those of you who were wondering.)

---

### Post by myturntohide on 2008-05-08
Is the 01000111 for God =P

---

### Post by 01000111 on 2008-05-09
> **myturntohide said:**
> Is the 01000111 for God =P

Nah... if that was the case, I'd make P=NP  :)

------------

There are 10 types of people in this world... those who understand binary, and those who don't.

01000111

---

