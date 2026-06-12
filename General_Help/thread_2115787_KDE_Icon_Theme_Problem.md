---
title: "KDE Icon Theme Problem"
date: 2013-02-13
forum: General Help
---

### Post by Roasted on 2013-02-13
I installed a few icon themes. All went well and I had no issues. But I noticed that within Dolphin, if I have previews enabled I can see that the themes are not changing properly with the directories that have previews. The other curve ball is the issue travels. The directories with the offset icons are not married to those specific icons. They'll change incrementally, but only one step behind the current theme. For example:

Icon theme B enabled (directories with preview show icon theme A)
Icon theme C enabled (directories with preview show icon theme B)
Icon theme D enabled (directories with preview show icon theme C)

As you can see in the screenshot, the directories showing previews are on the Elementary icon theme, whereas the rest of the directories clearly are not...

I've tried clearing the thumbnail cache as advised by another user... I just did an rm -r of all of the contents inside ~/.thumbnails. That made no difference though.

Any insight otherwise?

---

### Post by Roasted on 2013-02-14
Found it.

cd /var/tmp/kdecache-USER
rm icon-cache.kcache

Best to do this when not logged into KDE, but if I recall I think I did this while logged in and just logged out/back in and/or re-selected my new icon theme. Now that I think about it, I may have done both. Either way, the undoubtedly better way is likely to:

At login screen, CTRL ALT F1, log in to terminal mode, execute above commands. Once done, type "exit" and hit CTRL ALT F7 to return to GUI mode. Log in accordingly.

---

