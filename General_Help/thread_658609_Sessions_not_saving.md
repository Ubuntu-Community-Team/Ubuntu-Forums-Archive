---
title: "Sessions not saving"
date: 2008-01-04
forum: General Help
---

### Post by Vaelrith on 2008-01-04
I'm having a problem saving sessions.  I've done some research, and have tried to fix it using this command:
```
sudo chown nick ~/.config/autostart
```

but that doesn't work...

The problem is that I want to add AWN to the list of startup programs, however after I add it and close the sessions window, I can open the session window again and the list is all back to default.  I've even tried removing something from the list, then when i close and open the sessions window, the list is back to default and the entry I removed is back on there.

I tried using [this thread](http://ubuntuforums.org/showthread.php?t=286883), but that didn't help either.

Also when I open screenlets (System > Preferences > Screenlets) for the first time each session, it says something about the startup daemon not working, I think this may be related.

Thanks

---

### Post by linuxwizard on 2008-01-04
Check over this

[https://answers.launchpad.net/ubuntu/+question/12430](https://answers.launchpad.net/ubuntu/+question/12430)

---

### Post by Vaelrith on 2008-01-04
That seems to have fixed it, but I won't know until I log out and back in after I'm done downloading.

Thanks

---

