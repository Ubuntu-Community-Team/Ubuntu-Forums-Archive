---
title: "Mimetypes screwed up"
date: 2007-11-21
forum: General Help
---

### Post by rune0077 on 2007-11-21
So I get a bunch of new updates, and next thing you know, my mimetypes are alle screwed up. Go figure. 

The problem: all my files are now marked as unknown filetypes, and in the filemanager they just appear with the emptyfile-icon. The files are still working fine, and the moment I click on them, they revert back to their original, but this only last until I leave the folder again. So, this is not a huge critical problem or anything, just very annoying.

Anyone knows what the heck is happening here? I'm not 100% sure it was the update that did it, it just happened about the same time (it could also have been a reinstall of Compiz i did, though I don't see how that's possible).

---

### Post by rsambuca on 2007-11-21
One of these should work.  Try opening a terminal and then cut and paste the following commands.

You might try these first```
sudo update-mime-database
sudo update-desktop-database
```and if that doesn't work, try this```
sudo update-mime-database /usr/share/mime
sudo dpkg-reconfigure shared-mime-info
killall gnome-panel
killall nautilus
```

---

### Post by rune0077 on 2007-11-22
Thanks a bunch, that solved the whole mess. ... Ah well, almost. For some reason all my photos and other images didn't get fixed, except those used by the system (like wallpaper, icons and such). Everything else is back to normal, so that's great.

Again, thanks!

---

