---
title: "I know I can use desktop effects, but they aren't enabled by default on login"
date: 2008-04-28
forum: General Help
---

### Post by rainwalker on 2008-04-28
I've been using Beryl/Compiz since Edgy, so I know my computer is capable. I just installed Hardy, however, and effects are never activated when I log in. If I open a terminal and run ```
SKIP_CHECKS=yes compiz
``` effects will load successfully. I can close the terminal and Compiz will stay enabled, at least until I log out and back in again.

How do I set it to always enable the effects?

---

### Post by Fireblend on 2008-04-28
You can add commands that will automatically execute upon login at System->Preferences->Sessions. I guess you can create a new command with either that you're already using or with "compiz --replace".

---

