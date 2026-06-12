---
title: "gdm and .profile/bash function conflict"
date: 2008-06-11
forum: General Help
---

### Post by ersestur on 2008-06-11
Hi all,

I'm running gutsy and encounter the following problem after logging out from my gnome-session. The gnome session starts automatically at each reboot with auto-login enabled, btw.

So I log out and here comes GDM. When trying to login again, there's a clash with a function in my .profile and no windowmanager will start. I solved this problem by changing the default shell from dash to bash by "ln -sf /bin/dash /bin/sh". So now there's no clash with my .profile, but gdm now refuses to start any windowmanager with following .xsession-error:

/etc/gdm/Xsession: Beginning session setup...
/etc/gdm/Xsession: Executing dwm failed, will try to run x-terminal-emulator

Apparently GDM needs dash, but I need bash for my startup-scripts. Hmm.

thanks,
e

---

### Post by ersestur on 2008-06-12
One more thing, 

```

/etc/gdm/Xsession: Executing dwm failed, will try to run x-terminal-emulator
```

'dwm' can be substituted with any window-manager of course. I'm thinking of only executing my functions in .profile if bash calls them up, don't know how to manage that though.

thanks,
e

---

