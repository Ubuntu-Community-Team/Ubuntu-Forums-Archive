---
title: "Software updater doesn't show up"
date: 2014-01-28
forum: General Help
---

### Post by Rooster2000 on 2014-01-28
I commented in [this]("http://ubuntuforums.org/showthread.php?t=2172033#9") thread, but decided to open a new thread also.

For some reason, software updater hasn't showed up after I upgraded my Lubuntu from 13.04 to 13.10. I think it is running based on the hard drive activity every day, but the dialog (update notifier) just doesn't appear. If I start it manually from *System Tools -> Software Updater*, it opens normally, displays available updates (both security and other) and installs them correctly. Now it says that my system is up to date, but I cannot trust it to appear when new updates are available. What might cause this?

---

### Post by Rooster2000 on 2014-01-29
It seems that this is confirmed but not yet fixed bug.

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563)

In post #12 it is commented that

> I haven't found a configuration file that would cause Lubuntu to run update-notifier normally.

Well, meanwhile, got to search some alternative way to check at least security updates daily.

---

### Post by Rooster2000 on 2014-03-25
I tried from same thread [https://bugs.launchpad.net/ubuntu/+s...r/+bug/1046563]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1046563") what the latest post #13 suggested

> I found that there was a:
 Preferences > Default applications for LXSession > Options > Updates
option, but that it had "Activate Updates" as blank.  When I clicked on  the arrows at the right side of the the [button?], I noticed there was  an option "update-notifier".
I selected that, and then clicked on "Apply" and "Reload" (don't know  what that does), and when I exited the app, there was SoftwareUpdates on  my panel.
The next day it appeared as well.

For me it didn't notify updates right after I closed the window, but next day.
I thought I tried that one already, but I suppose I didn't clicked "Reload" after "Apply" (don't know what that does either :).

---

