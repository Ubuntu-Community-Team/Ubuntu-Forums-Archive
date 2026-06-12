---
title: "Unity + Chrome issue"
date: 2014-09-19
forum: General Help
---

### Post by andrew80 on 2014-09-19
Hi All,

Not sure if this is the best place if its not can one of the mods move it.

I've had Google Chrome installed on Ubuntu for ages and it worked fine. the other day I went into the unity menu, typed Chrome and two options come up, The first was Google Chrome the second was a link to a MP3 website. Clicking on the link did nothing at all. No issues.

So I noticed Chrome was no longer pinned to the launcher bar on the left so I pinned it to it, but when it pins it, it pins the link to the MP3 website rather than Chrome, so when I try to re open it.. it does nothing.

So after searching for ages on how to remove this link (its not a bookmark in Chrome or Firefox) I came across alacarte, Installed it and deleted the link! thank god.

All seemed well, only got Google Chrome as an option now :), So I just pinned my new installation of Chrome to the menu bar.. and the pinned item is actually this god damn link still.


Ubuntu 14.04, Brand new installation of Chrome 64bit

---

### Post by Frogs Hair on 2014-09-19
I would open the home folder, press Ctrl + H and locate the Google Chrome folder in .config and delete it . A new profile will be created when Chrome is opened, but you will loose your bookmarks, extensions, and settings. If Chrome is reinstalled this folder isn't removed so any errors caused by the profile aren't removed and the error comes back.

---

### Post by ajgreeny on 2014-09-19
I don't use google chrome but it may be advisable to rename, rather than delete, the configuration folder in ~/.config; that way you may be able to copy your bookmarks etc. to the new .config folder for chrome if you haven't already exported them to a file.

---

### Post by gifford on 2014-09-19
Either solution mentioned should work. If you have a gmail account with Chrome, and I would assume you do, all of your bookmarks and extensions will be restored when you 
sign into Chrome.

---

### Post by andrew80 on 2014-09-19
Tried the solution and it didn't work tried it two ways.

1. Delete the config folder and restart
2. Uninstall Chrome, Delete config folder, Re-install.

Yeh all my bookmarks etc are saved on the Google Servers.

---

### Post by andrew80 on 2014-09-19
Fixed it,

Simply un-installed Chrome, Deleted the config file and then did a search for any files with the word Google-Chrome in them.. removed everything to do with Chrome.

Re-installed and its worked as expected now and has allowed me to pin it to unity :)

---

### Post by andrew80 on 2014-09-19
Nope not fixed.. it was for a while then a few restarts later and its back.

---

### Post by andrew80 on 2014-09-20
Here's a fresh install of chrome
[[IMG]http://i274.photobucket.com/albums/jj266/baz88icf/Linux/Screenshotfrom2014-09-20120804_zpse8d5e8aa.png[/IMG]](http://s274.photobucket.com/user/baz88icf/media/Linux/Screenshotfrom2014-09-20120804_zpse8d5e8aa.png.html)

If I open it, it looks like this (see the MP3 description)
[[IMG]http://i274.photobucket.com/albums/jj266/baz88icf/Linux/Screenshotfrom2014-09-20120824_zpse4fff1d6.png[/IMG]](http://s274.photobucket.com/user/baz88icf/media/Linux/Screenshotfrom2014-09-20120824_zpse4fff1d6.png.html)

Completely removing Chrome, Removing all chrome files etc doesn't resolve this.. and it also starts doing it before I login to my Google Account.

---

