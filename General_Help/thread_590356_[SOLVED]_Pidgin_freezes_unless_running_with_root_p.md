---
title: "[SOLVED] Pidgin freezes unless running with root priviledges"
date: 2007-10-24
forum: General Help
---

### Post by raycosm on 2007-10-24
Ok, as the title states, Pidgin freezes if I don't run as root or gksu pidgin. It freezes about five to ten seconds after I open it, and I've tried disabling plugins and pidgin -n, it still freezes after a few seconds. Running Pidgin in terminal gives me these messages:

[INDENT]DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server![/INDENT]

...and it just repeats until I kill Pidgin. Running as su is a solution, and I wouldn't mind doing that if there's no other fix, but for security reasons, it's probably better for me to run Pidgin as a normal user.

---

### Post by kelbizzle on 2007-10-24
Try renaming the .purple folder to .purple.bak then see if the issue persist. This will make pidgin rebuild the folder.

---

### Post by raycosm on 2007-10-24
Well, it worked. Thanks

---

### Post by kelbizzle on 2007-10-26
your welcome

---

### Post by Garret88 on 2008-02-05
Disable the music tracker plugin and pidgin will work :)

---

### Post by atlanta800 on 2008-03-31
A little follow-up, I had the same problem, the culprit is definitely the music tracker plugin. Most specifically it trying to start up while having no music player to connect to (thus the dcop errors). My solution (without worrying about backing up your .purple directory) is just start your music player (I use amarok) THEN run pidgin and disable the music tracker.

Of course you don't necessarily have to disable the plugin, I did because I added pidgin to my session so it starts on log-in. But if you don't have the same kind of setup, just make sure your music player is running before you start pidgin!

---

### Post by cdean on 2008-04-28
Here's another related post on this issue.

[http://ubuntuforums.org/showthread.php?p=4824095](http://ubuntuforums.org/showthread.php?p=4824095)

And the related bug report, first reported in March 2008: [https://bugs.launchpad.net/ubuntu/+source/musictracker/+bug/199438](https://bugs.launchpad.net/ubuntu/+source/musictracker/+bug/199438)

---

