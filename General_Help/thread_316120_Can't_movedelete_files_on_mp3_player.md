---
title: "Can't move/delete files on mp3 player"
date: 2006-12-10
forum: General Help
---

### Post by Tampio on 2006-12-10
When I plugged in my mp3 player on 6.06 I could play the files just fine but I couldn't delete them or add new files. When I tried to delete them it seemed to work but when I replugged the mp3 player the files were there again. Same thing with adding files. Seemed to work fine but when I replugged the player the files weren't there. Both operations happened unnaturally fast. Any idea how I could make it work?

---

### Post by OffHand on 2006-12-10
> **Tampio said:**
> When I plugged in my mp3 player on 6.06 I could play the files just fine but I couldn't delete them or add new files. When I tried to delete them it seemed to work but when I replugged the mp3 player the files were there again. Same thing with adding files. Seemed to work fine but when I replugged the player the files weren't there. Both operations happened unnaturally fast. Any idea how I could make it work?

Might be a hidden .Trash folder where there deleted files are moved to instead of being deleted. If this is the case go in Nautilus to edit > preferences > behavior and select 'Include a delete command that bypasses the Trash'.

---

### Post by Tampio on 2006-12-10
That didn't do anything. Formatting the player got rid of the files, now if I just could put some new ones in there...

---

### Post by Tampio on 2006-12-13
So no one knows what can be done to fix this?

---

### Post by SteveF on 2006-12-13
> **Tampio said:**
> So no one knows what can be done to fix this?
Are you ejecting the mp3 player from the desktop (and waiting for write updates to finish)?

Also what kind of MP3 player?

Steve

---

### Post by Tampio on 2006-12-13
I plug it into an USB, wait a bit for it to auto-mount, drag-and-drop new files in there ("copying" happens instantaneously), unplug it --> no files in the player when I turn it on or replug it. 
And the player is this:
[http://www.reevoo.com/reviews/mpn/tangent/jukebox_256mb]("http://www.reevoo.com/reviews/mpn/tangent/jukebox_256mb")

---

### Post by SteveF on 2006-12-13
> **Tampio said:**
> I plug it into an USB, wait a bit for it to auto-mount, drag-and-drop new files in there ("copying" happens instantaneously), unplug it --> no files in the player when I turn it on or replug it. 
And the player is this:
[http://www.reevoo.com/reviews/mpn/tangent/jukebox_256mb]("http://www.reevoo.com/reviews/mpn/tangent/jukebox_256mb")
Usually you can't just unplug it.  You have to eject it.  You should right-click on the icon on the desktop and choose eject.  You should get a dialog (it may be quick) that displays while it writes out to the USB drive (if anything needs to be written out).

Copying sometimes copies to a cache that Linux keeps.  The cache may not get written out to the USB drive until you choose eject.

Steve

---

### Post by hikaricore on 2006-12-13
> **Tampio said:**
> I plug it into an USB, wait a bit for it to auto-mount, drag-and-drop new files in there ("copying" happens instantaneously), unplug it --> no files in the player when I turn it on or replug it. 
And the player is this:
[http://www.reevoo.com/reviews/mpn/tangent/jukebox_256mb]("http://www.reevoo.com/reviews/mpn/tangent/jukebox_256mb")

You have to unmount the drive by right clicking and choosing Unmount or the file copy process will not be processed correctly.  What you're doing is like dialing a phone number and hanging up right when the person you're trying to reach answers.  lol

Good luck,

--Aaron

---

### Post by SteveF on 2006-12-13
> **hikaricore said:**
> You have to unmount the drive by right clicking and choosing Unmount or the file copy process will not be processed correctly.  What you're doing is like dialing a phone number and hanging up right when the person you're trying to reach answers.  lol

Good luck,

--Aaron
Just to clarify a little, unmount vs eject will depend on which desktop you use (Ubuntu or Kubuntu ie. Gnome or KDE).  They do the same thing, just have different labels in the menu.

Steve

---

### Post by Tampio on 2006-12-13
Ooh, it works like that. Thanks a lot.

---

### Post by hikaricore on 2006-12-13
> **SteveF said:**
> Just to clarify a little, unmount vs eject will depend on which desktop you use (Ubuntu or Kubuntu ie. Gnome or KDE).  They do the same thing, just have different labels in the menu.

Steve

Woops thanks for mentioning that, the gnome/kde thing didn't cross my mind when posting.  :)

---

