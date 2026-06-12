---
title: "Have gdesklets not be affected by show-desktop"
date: 2008-02-12
forum: General Help
---

### Post by Izek on 2008-02-12
How can I make it so that my gdesklets stay on the desktop when I "show desktop"?

---

### Post by torgrot on 2008-02-13
Sorry about that, I misunderstood.  They are after all a window, and show desktop hides all the windows.

Under System-> Preferences->Sessions Click Add and then name it.  How about gdesklets?  and then command should be /usr/bin/gdesklets start

torgrot

---

### Post by Izek on 2008-02-13
> **torgrot said:**
> Sorry about that, I misunderstood.  They are after all a window, and show desktop hides all the windows.

Under System-> Preferences->Sessions Click Add and then name it.  How about gdesklets?  and then command should be /usr/bin/gdesklets start

torgrot

I know how to start gdesklets when Ubuntu starts -_-

---

### Post by apetresc on 2008-02-13
If you're using Compiz/Beryl, then it's easy to do. Check out [this thread](http://ubuntuforums.org/showthread.php?t=412812) That last post is both hilarious and informative :)

---

### Post by Izek on 2008-02-13
> **AdrianP said:**
> If you're using Compiz/Beryl, then it's easy to do. Check out [this thread](http://ubuntuforums.org/showthread.php?t=412812) That last post is both hilarious and informative :)

Which one out of these would be a gDesklet?

```
type=toolbar | type=utility | type=dialog | type=normal
```

---

### Post by rosslev on 2008-06-19
i'd like to know that too, which if any of these would a gdesklet be?

---

### Post by Izek on 2008-06-22
> **rosslev said:**
> i'd like to know that too, which if any of these would a gdesklet be?

class=Gdesklets-daemon
type=Normal
role=Null
name=gdesklets-daemon
title=gdesklets-daemon

Is the list of things a gdesklet is. However, with the new ccsm, there is no line for "exclude" in the show desktop plugins.

---

