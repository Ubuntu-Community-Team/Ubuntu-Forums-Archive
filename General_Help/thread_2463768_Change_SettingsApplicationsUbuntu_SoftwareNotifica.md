---
title: "Change Settings:Applications:Ubuntu Software:Notifications from command line"
date: 2021-06-17
forum: General Help
---

### Post by sampsonats on 2021-06-17
I want to be able to change various gsettings from a script.  For example, Settings:Applications:Ubuntu Software:Notifications.

I would like to be able to watch any changes, go to the gui and make changes and then copy the path from the watch results.

I tried 
```
gsettings monitor com.ubuntu.notifications.settings.applications
```
and then modified the setting with the gui but the monitor command didn't display anything.

I really like the
```
dconf watch /
```
concept but it doesn't pick up this setting change either.

As I think I understand it, dconf is just a database for gsettings.  Could you tell me the architecture of how all this is organized?

Is there a way to do what I am trying to do?

Thanks!
Todd

---

