---
title: "GNOME panel layout jumbles up"
date: 2007-01-15
forum: General Help
---

### Post by allwin on 2007-01-15
I configured a number of items in my GNOME panels at the top and bottom of the screen.  Let's say that when I logged off the last time, their order was A, B, C, D.

After rebooting, all of a sudden, the items in the panel come up in D, C, A, B order!  IOW, my application menu (ubuntu circle icon) instead of being on the left of the panel, is now in the middle...the time which was on the right is now displayed on the left.

Where can I go to change this back, or did I overlook an option which sorts by the name of the program being launched or something like that?

---

### Post by hikaricore on 2007-01-15
Eh, you could try right clicking on the items after re arranging them and choosing the "lock" option to lock them in place.  But sadly gnome just does this sometimes because in my opinion it's configuration files suck.  Hope this helps.

---

### Post by psi36 on 2007-02-06
I have the same problem.

hikaricore, somehow your reply doesn't really satisfy me. ;) 
Bad luck, not much to be done about it? 

Surely there must be some way to fix this? 
If this happens often, then someone must have found a solution...

In the Configuration Editor I've edited apps/panel
This doesn't change anything, but I guess I might have to restart for these changes to become active?

---

### Post by psi36 on 2007-02-06
OK, I logged out and in again and I'm on the right track. Now my volume control is to the left, with my starters (Evolution, Firefox, etc.) and the red Log Off button is stil somewhere near the middle.

Problem is I can't find which setting in the Configuration Editor is for the Log Off button. Does anyone know this?

I'll just explain shortly what I did before log out/in: Open the Configuration Editor: Applications > System Tools (if it's not there you can add it in Menu Layout, under System > Preferences). In Configuration Editor you go to apps/panel/applets and there you check pannel_right_stick for the items you want to the right. The position field controls in what order they apear (0 being the most right if you choose pannel_right_stick). BTW: it's not the number of pixels, as the Long Description says.

If I could only find out where I can change these settings for the Log Off item I could put that red button back where it belongs...

---

### Post by psi36 on 2007-02-06
OK, I ended up unlocking, moving and locking again the applets manually (by right clicking on the items). Actualy that is much handier then the Configuration Editor route I explained above.

But at least now everything is back in place, including the Log Out button! :)

---

### Post by hotdoog on 2007-09-04
I have this same problem too. I find it annoying/tedious to have to fix it regularly, because I've got a dozen or so icons and you can't do it all at once.

Isn't there one config file that dictates the position of the icons? Can't that file be backed up in a straightforward way? I don't understand the panel well enough to know, but it seems that is isn't so simple. but even a set of files could be backed up.

this reminds me of my windoze days the icons on the desktop would sometimes rearrange themselves. There was some 3rd party demo program I would get to save the state of the desktop in case that would happen. Seems like a simple program like that would be useful for gnome.

In linux couldn't it just be a bash script? but then, you'd have to know what files to backup. does anyone know?

What other issues could there be? I guess these same files might have other configurations that you wouldn't want to backup in the same way...

Anyway, i'm still pretty new to all this, but it seems like we ought to be able to fix it. But then I guess we'd have to fully understand the gnome panel and when I look at documentation for stuff like that i just get overwhelmed and give up. I'd prefer a simple hackerish solution.

---

### Post by olejorgen on 2007-09-04
Ok.. it got to be some way of fixing this.. I'm using a tablet pc, and everytime I rotate my screen to portrait the menu f**ks up.

Changing the settings in gconf-editor does not work (dynamically).
gnome-panel has no useful command options.

---

### Post by seanf on 2007-11-19
> **olejorgen said:**
> Ok.. it got to be some way of fixing this.. I'm using a tablet pc, and everytime I rotate my screen to portrait the menu f**ks up.

Changing the settings in gconf-editor does not work (dynamically).
gnome-panel has no useful command options.

[https://wiki.ubuntu.com/PanelSwitcher](https://wiki.ubuntu.com/PanelSwitcher)

---

