---
title: "Run Dropbox app simultaneously under different (uid), while in current session ?"
date: 2014-08-13
forum: General Help
---

### Post by funnyfuntimes on 2014-08-13
So im testing the Dropbox app on Xubuntu:

Within the Dropbox folder is a 800mb encrypted TrueCrypt volume, for backups.{yes, i know it only syncs to cloud when unmounted}

[1]Is it possible to run it simultaneously under a different user name(uid)non-administrator, while in a current session?{ due to X11 security issues= password sniffing}

User-1(Tod), uid 1000, (this is the main desktop,current session).
User-2(David)[non-administrator], uid 1001, (to isolate running app from main desktop).


[2]Can this "start-stop-daemon" i heard rumor of do this, or something else? ...is there a GUI for it?
{i also figure i wont see the dropbox app or its indicator icon on the main first-user desktop}

If the above can be done, the idea is to then restrict access to a shared "/Dropbox" folder using (ACLs) via "Eiciel".


At a later point i will further lock Dropbox down with a Apparmor profile.

---

