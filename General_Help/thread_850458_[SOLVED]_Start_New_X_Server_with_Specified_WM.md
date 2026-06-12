---
title: "[SOLVED] Start New X Server with Specified WM"
date: 2008-07-05
forum: General Help
---

### Post by timo1023 on 2008-07-05
Hello,

I know I can start a new X server with
```
sudo startx --:1
```

However, that starts a new X server with Gnome/Metacity as the WM. I would like to start a new X server with a specified WM. How can I do this?

This is usually the kind of thing I would mess around with and figure out myself, but Ubuntu gets all buggy when I mess around with the 'startx' command and make it fail.

Thanks.

---

### Post by kellemes on 2008-07-05
```
startx /usr/bin/gnome-session
```
or
```
startx /usr/bin/startkde
```
or
```
startx /usr/bin/fluxbox
```

etc..

You need to find the start script for the particular wm and use it with startx.

Edit: By the way.. you beter run startx without sudo.. as user that is.

---

### Post by timo1023 on 2008-07-05
Thanks, kellemes, that worked fine. I did have to modify /etc/X11/Xwrapper.config to read 
```

allowed_users=anybody

```
in order to be able to start the X server as a regular user.

---

