---
title: "[SOLVED] Help with making a shortcut to xscreensaver"
date: 2008-03-22
forum: General Help
---

### Post by Playa1313 on 2008-03-22
Hello, I either want to make a shortcut to run xscreensaver or add to/replace the lock-screen option in the "logoff, switch user, lock screen or power down the computer" panel.

However, I have looked all over google and cannot find someone who has written about creating a shortcut for xscreensaver.  And you have probably noticed I don't know what the "logoff, switch user, lock screen or power down the computer" panel is called, so I can't look to see if there's any way to customize that.

Any help would be greatly appreciated

I assume that I need a script to be run for xscreensaver, but I am not sure how to make one.

Also, another alternative is removing the password required for waking up from lock using that panel, but I can't find anything about that either.

Thank you

---

### Post by scragar on 2008-03-22
just set a launcher to run the command:
```
 gnome-screensaver-command -a
```to launch the normal screensaver
or:
```
 gnome-screensaver-command -l
```to lock the screen

both may be assigned to key combo's using system>preferences>keyboard>shortcuts

---

### Post by Playa1313 on 2008-03-22
Thank you very much!! Exactly what I needed :)

Only thing I changed was 

```
Gnome-screensaver-command -a
```

to

```
xscreensaver-command -a
```

Thank you, thank you! lol ^.^

---

