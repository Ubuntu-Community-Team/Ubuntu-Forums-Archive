---
title: "beryl"
date: 2007-01-24
forum: General Help
---

### Post by n8ek on 2007-01-24
when beryl is running i could hover the mouse over the task bar and a little popup window would appear showing you what was in the other open or minimised window, it is now not there anymore could it be due to an update or a program error?

Thanks in advance

---

### Post by JoshuaH1 on 2007-01-24
Check to make sure its turned on.

Right Click on Beryl icon > Beryl Settings Manager > Extras Tab > Window Thumbnail

---

### Post by Dave Burbank on 2007-01-24
I think they may have removed this on the last update (0.2.0 beta2).

"beryl-settings>extras>windows thumbnail" no longer appears.

"beryl-settings>general options>window thumbnail" doesn't seem to do anything.

Anyone have this working for 0.2.0 beta2?

---

### Post by JamieC on 2007-01-24
Yes, I do. It is now contained in the package 'beryl-plugins-extra'. Open a new terminal and type:
```

sudo apt-get install beryl-plugins-extra

```

Then reload the window manager and the thumbnails should appear.

---

### Post by Robor on 2007-01-24
> **JamieC said:**
> Yes, I do. It is now contained in the package 'beryl-plugins-extra'. Open a new terminal and type:
```

sudo apt-get install beryl-plugins-extra

```

Then reload the window manager and the thumbnails should appear.

Thanks Jamie!  :)

---

### Post by Dave Burbank on 2007-01-24
Yes, thanks JamieC.
Is this package new as of 0.2.0 beta2, or did I just miss it?

---

### Post by n8ek on 2007-01-24
done it thanks a lot people

---

