---
title: "file manager right click shows old deleted file"
date: 2014-01-16
forum: General Help
---

### Post by JDix531 on 2014-01-16
[http://i.imgur.com/VoW2Uut.png](http://i.imgur.com/VoW2Uut.png)

This is bugging the heck out of me! I figure there is probably a config file or something I can edit. The backstory is that I accidentally dragged a file to the shortcuts-side-bar in the file explorer from the documents folder it was in. I managed to remove it from there by deleting the file then clicking on the shortcut. The file manager seemed to recognize it didn't exist anymore and it was removed gracefully. This menu still contains the broken shortcut to a file that no longer exists.

Suggestions? Thanks a ton in advance.

PS. Pretty advance computer user but newer to linux so I guess keep your replies with that mind set. If you say a conf files name I would also appreciate the location :P

---

### Post by mc4man on 2014-01-16
Might be useful to say what release of Ubuntu you're on as things change a bit in this regard (location of file
The bookmark should of be removed from the quicklist automatically , maybe try a log out/in
Otherwise locate the 'bookmarks' file, in 13.10/14.04 it's in .config/gtk3/ as per screen, remove the entry, ect. (ex. here would be highlighted entry
(if unable to locate search home directory for - 
bookmarks

---

### Post by JDix531 on 2014-01-16
Thanks a lot, I havn't fixed it yet because I'm not at my laptop but I'll let you know in a few minutes. Also I'm on 13.10

lastly i have tried logging in and out its been there a few days now

---

### Post by JDix531 on 2014-01-16
Huzzah! You're a hero! Where would I find this information on my own? I had a little trouble searching the nets.

Also, I had to "cd ~/.config/gtk-3.0" to get there as I couldn't find it in the browser. Are dirs leading with "." hidden? Thanks!

---

### Post by deadflowr on 2014-01-16
> [COLOR=#000000] Are dirs leading with "." hidden? Thanks![/COLOR]

Yep.
Any file or folder with a dot will be hidden by default(or should be hidden by default).
In the file manager pressing ctrl+h will show hidden file/folders.
It should also be a listed option in the file manager's settings.
Look at the down arrow next to the cog in the top section of Files.
(the cog at the far right side of the top section.)
The "show hidden files/folders" should be at the bottom.
Click on it to enable/disable.

---

### Post by JDix531 on 2014-01-16
HAHA Jeesh, I know I checked the settings but not the arrow. Oh well! You guys are great!

---

