---
title: "Attempting to run tightvncserver, odd icon behavior"
date: 2014-01-23
forum: General Help
---

### Post by nexpe on 2014-01-23
Hi, I am having trouble accessing my Ubuntu 12.04 server via VNC. I attempted to set up tightvnc server using the guide at [https://www.digitalocean.com/community/articles/how-to-setup-vnc-for-ubuntu-12](https://www.digitalocean.com/community/articles/how-to-setup-vnc-for-ubuntu-12) and got up to the point of connecting to the VNC server (before setting up SSH forwarding) and witnessed some odd desktop behavior

All launchers opened from the desktop in vnc give the following error
> Launch Error: Failed to change to directory '/root' (permission denied) 
But opening the same launcher in the same location as the same user from Thunar in VNC works just fine. If i connect physically to the machine and login as the vnc user, all desktop launchers behave normally, so I suspect my error is in how i am running the server, but reading back over the setup it looks like everything is running as the vnc user.

Does anyone have any idea why this is happening?

---

