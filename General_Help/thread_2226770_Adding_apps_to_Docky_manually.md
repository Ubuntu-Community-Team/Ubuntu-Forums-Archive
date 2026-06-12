---
title: "Adding apps to Docky manually"
date: 2014-05-28
forum: General Help
---

### Post by Tony_Lillie on 2014-05-28
Ubuntu 14.04 with gnome-3 and the Docky app.

I'm fairly new to using Docky, and have found that sometimes it is necessary to add apps manually as the "pin to Dock" feature doesn't always work. In those cases I use the gconf-editor to access the Docky launchers list and simply add the path manually, i.e. /usr/share/applications/someapp.desktop

This needs to be done with Docky closed or it will overwrite these actions. Upon restarting Docky the app is on Docky as it should be.

Here's the problem: I'm trying to add Teamviewer 9 through this manual addition procedure, but I can't seem to get the path right. It's definitely in /usr/share/applications but the exact syntax for the name is eluding me. I've tried several variations including teamviwer9, team-viewer9, teamviewer-9, team-viewer-9, Teamviewer9, Teamviewer-9, TeamViewer9 and many others. All of these ending with  ".desktop". I'm beginning to wonder if the name is something entirely different??

So, I need help discovering the correct name for the app, or some other direction if I'm missing something.

Any help would be greatly appreciated.

---

### Post by Tony_Lillie on 2014-05-29
It's amazing how the obvious solution sometimes eludes us. I was looking at the app names in the Nautilus gui, duh!!  As soon as I looked it up via the command line I got the answer, it's oddly named for sure: teamviewer-teamviewer9.desktop

Gotta love the CLI!!!

Adding this edit just because: Isn't it odd (stupid, painful, counterproductive, insert derogative here) that the gui would fail to accurately report the name of the item. I realize that it's a complicated thing getting the gui to do things like the cli, which is why the cli is often the more powerful way to do things, but seriously... reporting the complete and accurate name of a file shouldn't be that difficult.

Why does this matter? Why the rant? Because Ubuntu continues to add layers of complexity without making the obvious things simple enough for mainstream users. Personally, as a long time tech guy I love it, but this situation is exactly the kind of thing that stops me from converting "common" Windows users to Ubuntu. Most of them would go into cardiac arrest if confronted with a cli. Sorry, but this instance really grieved me and once again made me question if Ubuntu will ever... ever be a viable alternative for non-techy mainstream users.

---

### Post by Joe_Johnston on 2015-03-09
This was so helpful and thank you for making this known!

---

