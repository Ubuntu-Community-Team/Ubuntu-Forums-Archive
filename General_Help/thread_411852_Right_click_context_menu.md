---
title: "Right click context menu"
date: 2007-04-17
forum: General Help
---

### Post by heingericke on 2007-04-17
Using Edgy with Gnome. Your basic 6.10 install and no mods.

I was hoping if someone could tell me if I can modify the right click context menu on the desktop to include an option to send a file/folder to another folder similar to KDE.

I recently made the the full transition to Ubuntu after dual booting for a while with OpenSuse and the KDE environment had a right click option to move or copy a file/folder from the desktop to wherever I wished.

On the Gnome desktop (which I like) all I see is a "send to..." option which opens Evolution to send via e-mail and "move to the deleted items folder".

Thank you.

And it was my wifes decision to move to Ubuntu full-time.

The best decision she made.... next to marrying me of course. :D

---

### Post by beerorkid on 2007-04-17
my wife is an ubuntian as well.  Only windows to update our logitech remote.

pretty cool idea you have there.  Found some info on it.

from this thread: [http://ubuntuforums.org/showthread.php?t=361732&highlight=nautilus+scripts](http://ubuntuforums.org/showthread.php?t=361732&highlight=nautilus+scripts)

looks like this is what you are looking for.
[http://ubuntuforums.org/showthread.php?t=101870](http://ubuntuforums.org/showthread.php?t=101870)

and this has some more
[http://ubuntuforums.org/showthread.php?t=344678&highlight=nautilus-script](http://ubuntuforums.org/showthread.php?t=344678&highlight=nautilus-script)

---

### Post by matigol on 2007-04-17
Maybe nautilus-actions. No ? 

With them, i can put an image as wallpaper on one click.

Maybe you can look after that...

---

### Post by heingericke on 2007-04-17
> my wife is an ubuntian as well. Only windows to update our logitech remote.

pretty cool idea you have there. Found some info on it.

from this thread: [http://ubuntuforums.org/showthread.p...utilus+scripts](http://ubuntuforums.org/showthread.p...utilus+scripts)

looks like this is what you are looking for.
[http://ubuntuforums.org/showthread.php?t=101870](http://ubuntuforums.org/showthread.php?t=101870)

and this has some more
[http://ubuntuforums.org/showthread.p...autilus-script](http://ubuntuforums.org/showthread.p...autilus-script)


Thanks.

That is extremely useful.

The KDE environemet had an arrow after "move to" and "copy to" that opened a secondary context menu like when you use the drop down menu at the top sytem>preferences or system>administration.

I must not be greedy. Thanks.

---

### Post by tonywhelan on 2007-04-24
> **heingericke said:**
> Using Edgy with Gnome. Your basic 6.10 install and no mods.

I was hoping if someone could tell me if I can modify the right click context menu on the desktop to include an option to send a file/folder to another folder similar to KDE.

I recently made the the full transition to Ubuntu after dual booting for a while with OpenSuse and the KDE environment had a right click option to move or copy a file/folder from the desktop to wherever I wished.

On the Gnome desktop (which I like) all I see is a "send to..." option which opens Evolution to send via e-mail and "move to the deleted items folder".


Take a look at my partial solution at this thread:
[http://ubuntuforums.org/showthread.php?t=417978&highlight=nautilus+actions](http://ubuntuforums.org/showthread.php?t=417978&highlight=nautilus+actions)

Note that these two scripts are good for Copying or Moving FILES only. I haven't yet had the time to adapt them to moving folders as well, though it probably wouldn't take long to do it. Hence when you set up the script in Nautilus Actions Configuration, you should set it to only display these options on the menu when  files are selected, not a folder. Otherwise the script will tell you it can't do it.

---

