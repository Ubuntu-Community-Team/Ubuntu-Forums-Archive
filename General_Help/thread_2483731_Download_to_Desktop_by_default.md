---
title: "Download to Desktop by default?"
date: 2023-02-07
forum: General Help
---

### Post by klundermann on 2023-02-07
Often when I open a download location or existing file in an app, the app chooses my home directory by default.  It would be much more convenient if I could get apps to default to Desktop or Documents.  Is there any way of doing this without find the default settings for each app?

---

### Post by TheFu on 2023-02-07
Perhaps.

It will be OS-release,  DE and application specific.  

Some programs will not have access to your Desktop directory, so the cannot write anything there. It is part of snap security to prevent that access.

So, if the stars, moons, and planets all align, then there is a setting for downloads in $HOME/.config/user-dirs.dirs
Look for the 
```
XDG_DOWNLOAD_DIR="$HOME/Downloads"
```
setting.  Change the location, logout, login and see if that works.  I can't test with 22.04 and firefox currently because it is a snap package and refuses to run over remote X11.  Sigh.  

Snap packages run in a constrained environment, so they are limited where they can read and write.  The constraints are set by the snap package team.  There are non-snap versions of Firefox.  Alas, you didn't say which program you were using.

---

