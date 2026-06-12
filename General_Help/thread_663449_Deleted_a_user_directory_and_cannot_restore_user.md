---
title: "Deleted a user directory and cannot restore user"
date: 2008-01-10
forum: General Help
---

### Post by dark_ixion on 2008-01-10
Those who are sensitive to horrifying butchery on Linux, turn your eyes away now.

Bascially, I installed Compiz on Gutsy and noticed the top bar of all the windows was missing, so uninstalled it and everything was back to normal for my own login, but not the login of the other user on the PC.  The other user still had the top bar missing on the windows, except now each window was pinned to the top left-hand corner of the GUI, so the menus couldn't even be accessed.  Compiz had been completely removed and the desktop effects were disabled.  I checked that option for both users.  I even rebooted just in case it was caching some configuration that had been updated.

I decided to delete that user and recreate it.  The problem persisted because it didn't erase the user's directory in the home directory.... so I deleted that directory as root.  I then tried to add the user back in again.  It didn't complain, but then it didn't add the user to the list either (this all being done with the GUI).  I decided to create that user's folder again but without any content.  I then tried adding the user back in, but still no joy.

What have I done?  How can I create my user again?

---

### Post by dark_ixion on 2008-01-11
I somehow got the user created, but the problem with the top bar missing persisted.  I restarted metacity which restored the bar (with --replace) but it didn't stay like that after logging out.  I ensured metacity was set with restart in the services list, but then I noticed none of the services were set up with restart or settings.  This was the case for every new user I added, and it would be a world of pain to manually correct it each time, so I decided to nuke the install and start from scratch.

---

