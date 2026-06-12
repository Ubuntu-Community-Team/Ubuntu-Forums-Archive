---
title: "thunderbird or ??"
date: 2020-06-18
forum: General Help
---

### Post by jgw on 2020-06-18
I have been using thunderbird for my mail client for years.  Its made changes and strange things seem to be occurring.  The latest was to add "ï¿½" after every '.'   Apparently the solution is to deal with encoding which apparently needs to be set at UTF8.  I have no idea where, or how to do that and even after that is fixed who knows what comes next.  Anyway,  I was wondering if I should just change email clients and, if is, which one?.  I run most of my email through yahoo and they also have an email client (I also have a gmail account). 

thank you..............

---

### Post by TheFu on 2020-06-18
I use **claws-mail** on a desktop and **k9-mail** on android.  Don't know whether those work with any huge email providers or not.  Claws lacks some basic features, but I won't use that bloated other tool trying to be MS-Outlook that Canonical loads, Evolution.

I'd rather use thunderbird, but they decided our internal email server's self-signed cert wasn't sufficient though it is never accessible on or from the internet.  Hundreds of popup messages for the same "problem", that isn't actually a problem isn't acceptable. I really miss the Lightning addon to access our calendar system.

As for controlling the LANG, there are 2 places - or one - on a server.
**sudo dpkg-reconfigure console-setup**
I'd guess it would be controlled for a GUI somewhere in the Settings/Preferences, but don't really know.

---

### Post by SeijiSensei on 2020-06-19
Preferences > Display > Advanced will let you set the default character-encoding  for outgoing mail. On my machine it's set to "Unicode (UTF-8)".  If that's not the setting you have, I'd choose that since all of Ubuntu uses UTF-8.  I'd avoid Windows characters sets or ISO-8859-1. The latter is the default for incoming mail, though most email contains a "Content-Type" header which declares the chararacter set used in that message.  If you've never done so, open a message, then hit the "More" button and choose "View Source."  You'll see all the message headers including Content-Type.

---

### Post by T6&amp;sfpER35% on 2020-06-19
give [bluemail](https://www.bluemail.me/) a try too,i'm using it and don't have any problems. i have it on my android too so everything syncs nicely between my phone and desktop.
available for ANY OS.

---

