---
title: "XFCE - Why Chrome starts up with login?"
date: 2014-02-13
forum: General Help
---

### Post by WinterMadness on 2014-02-13
This is annoying. I dont know why this would happen.

I've gone to Settings -> Session and Startup -> Application Autostart

Chrome is not in the list at all.

Any other ways to check whats starting up with my login?

Im not saving my session upon logout either.

---

### Post by slickymaster on 2014-02-13
> **WinterMadness said:**
> <...snip...>
Any other ways to check whats starting up with my login?<...snip...>

Check for **.desktop** files in ```
/usr/share/applications
``````
/.local/share/applications
``````
/etc/xdg/autostart/
```

---

### Post by WinterMadness on 2014-02-13
should i delete the .desktop files or something?

---

### Post by vasa1 on 2014-02-13
Also, go into *chrome://settings*, *Show advanced settings* and see if you have *Continue running background apps when Google Chrome is closed* ticked or unticked.

---

### Post by slickymaster on 2014-02-13
> **WinterMadness said:**
> should i delete the .desktop files or something?

No, do not delete them. Those are the places to check what applications are starting up when you login.

---

### Post by Toz on 2014-02-13
Clear your saved sessions cache anyways - it can get corrupted.

If running 13.10 (Xfce 4.10) or later: Settings Manager -> Session and Startup -> Session tab -> "Clear saved sessions"

If running anything earlier, you need to (before you login):
1. Ctrl + Alt +F1
2. log in to text session
3. Run:
```
cd .cache
rm -rf sessions
```
4. Ctrl+Alt+F7
5. Log in to gui session and check.

---

### Post by CaptainMark on 2014-02-14
This drives me up the wall, I've tried everything and still maybe 30% of the time I still get a terminal open on login, eventually just learned to live with it, have an intention to sort it out eventually

---

