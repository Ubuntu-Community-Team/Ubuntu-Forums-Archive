---
title: "How to start MythTV on boot"
date: 2007-01-20
forum: General Help
---

### Post by dcroxton on 2007-01-20
I have MythTV working on my Edgy box and I'm trying to get it to automatically wake up and shut down the computer to record programs.  The wake up and shutdown appear to be working fine (using acpi), but mythtv-backend doesn't start when the computer boots up.  I have a symlink in rc5.d, S80mythtv-backend.  If I try ./S80mythtv-backend start, it works fine.  (Without the "start" argument, it doesn't do anything, but the same applies to all the other startup symlinks, so I presume this is taken care of by the boot process somewhere.)  So why isn't it starting when I boot up?

I can't find anything in the logs, either in mythbackend.log or in any other logs -- admittedly, I'm not sure where to find the boot log information, that might help a lot.

If anyone has any suggestions, I would be grateful.

Sincerely,
Derek

---

### Post by Roebi on 2007-01-24
Are you booting up into Mythwelcome? Normally this should start up the backend for you.
OR, are you logging in automaticly? I experienced that when I would log in too quickly, the backend wasn't ready, and I would receive an error message.
So I have the machine wait 10 seconds now before it logs in.

Roebi

---

