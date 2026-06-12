---
title: "Suddenly lost all my desktop settings"
date: 2007-09-14
forum: General Help
---

### Post by goldtech on 2007-09-14
I've just lost all my desktop settings. The shortcut launchers, the background, and the "arrangement" are all gone. I just booted up and it was gone!

New user and very surprised this happened. Any ideas what to do?

When I look at my /home/desktop I see the icons I should have but don't and if I  add launchers/shortcut to this weird desktop I have - they get added to my /home/desktop but I don't see them!

It's like I'm using another desktop - happened when i booted up and logged in.

---

### Post by PointSource on 2007-09-15
Are you using ubuntu or kubuntu? I think I can help with ubuntu but I have no Idea about kubuntu.
The desktop icons are placed on the desktop by nautilus (in a different mode to what is usually displayed, ie the file browser window). Maybe your session file is corrupt and is not loading nautilus for you. If so, then I would suggest removing your session file to regenerate a new one that is perhaps not corrupted.

```
rm ~/.gnome2/session
```

If you have made specific modifications to this, you may want to save a backup copy.

---

