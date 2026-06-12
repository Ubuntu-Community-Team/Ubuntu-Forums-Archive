---
title: "password"
date: 2015-02-28
forum: General Help
---

### Post by ma6456 on 2015-02-28
Since some time,no specific incident, ubuntu (14.4) will not accept (right) password when waking up from sleep. Will accept password when rebooting.
Seit einiger Zeit, unbestimmt, nimmt Ubuntu das Passwort nach Bereitschaft nicht an. Bei Neustart wirdPasswort aber akzeptiert.

---

### Post by TheFu on 2015-02-28
Thought I had the same issue ... turned out to be related to having an encrypted file system.  I have to give it 1-2 minutes for the file system to catch up (decrypt) with the GUI - then I can enter the password, post-sleep, and all is fine.  The password entry field doesn't accept anything until that time.

Or ... it could be a bug in ibus.  I had an issue where my password manager "auto-type" wouldn't work on 1 system here, but worked fine on another.  Removed ibus* packages, logged out, logged back in and everything has been working since.  I only use English, so not having ibus hasn't been an issue ... that I've noticed.  Of course, the ibus thing may not be related at all. There is a bug about it: [http://ubuntuforums.org/showthread.php?t=2228674](http://ubuntuforums.org/showthread.php?t=2228674) be certain to read the links in that link for more details.

Or it could be something completely different?

---

