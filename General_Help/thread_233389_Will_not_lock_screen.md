---
title: "Will not lock screen"
date: 2006-08-10
forum: General Help
---

### Post by rekahsoft on 2006-08-10
Hi all...i have came uppon a problem...i always lock my screen when i leave my computer...it always used to work until yesterday when i just stoped working...i checked to see if the shortcut changed and i set it to what i want and it still doesn't lock the screen...how do i fix this?

---

### Post by ciscosurfer on 2006-08-10
Go to System > Preferences > Screensaver and make sure the "Lock screen when screensaver is active" box is selected.  This could be the problem.

---

### Post by rekahsoft on 2006-08-10
Nope....not the problem...i have the lock screen when screensaver is active radio button selected...

---

### Post by 23meg on 2006-08-10
Does ```
gnome-screensaver-command -lock
```work?

---

### Post by ciscosurfer on 2006-08-10
@23meg
Did you mean this instead?```
gnome-screensaver-command --lock
```

---

### Post by rekahsoft on 2006-08-10
it says that screensaver is not running...i will restart and see if that helps...brb

---

### Post by rekahsoft on 2006-08-10
ok...i figured out why it was not working...before i restarted i pressed ctr+alt+backspace to restart X...screensaver did not start up again :) thanks for the help guys :)

---

