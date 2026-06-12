---
title: "mplayer installation problem in firefox"
date: 2008-06-30
forum: General Help
---

### Post by mvanbeek on 2008-06-30
I just installed mozilla mplayer in Hardy and then when opening Firefox (3b5), my bookmarks were gone and the history was as well.  Couldn't even use the back button while browsing.  When I removed mplayer, Firefox was back to normal.  Anyone else heard of this problem?

---

### Post by Vivaldi Gloria on 2008-06-30
> **mvanbeek said:**
> I just installed mozilla mplayer in Hardy and then when opening Firefox (3b5), my bookmarks were gone and the history was as well.  Couldn't even use the back button while browsing.  When I removed mplayer, Firefox was back to normal.  Anyone else heard of this problem?

I first enabled medibuntu and then used the commands

```
sudo apt-get remove --purge totem-mozilla

sudo apt-get install mplayer mozilla-mplayer
```

and I have no problems at all.

---

### Post by mvanbeek on 2008-06-30
Thanks a lot for the help, that seemed to work for me.

---

### Post by Vivaldi Gloria on 2008-06-30
> **mvanbeek said:**
> Thanks a lot for the help, that seemed to work for me.

You're welcome.

---

