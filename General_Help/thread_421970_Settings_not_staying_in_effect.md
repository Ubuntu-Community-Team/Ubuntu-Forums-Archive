---
title: "Settings not staying in effect"
date: 2007-04-24
forum: General Help
---

### Post by ~LoKe on 2007-04-24
If I customize Firefox and move around the buttons, remove the google search field, etc, then close the browser and re-open it, my changes are gone.  Firefox goes back to how it used to be.

If I load up a game (Enemy Territory) and change the resolution or other settings, close the game, then re-open it, it's back to the way it used to be.

Also, a separate problem, when I try to bookmark something, I get duplicate locations.
Bookmarks
Bookmarks Toolbar Folder
------------------------------------------
Bookmarks
Bookmarks Toolbar (notice the missing "Folder")

This is pretty annoying.

---

### Post by ~LoKe on 2007-04-24
Bump.

---

### Post by ~LoKe on 2007-04-25
:(

---

### Post by strabes on 2007-04-25
Can you post the output of this command? ```
ls ~/.mozilla/firefox/
```

The first problem might have something to do with your firefox profiles. However, because you're having the same problem in two programs at once, I'm leaning towards thinking it's a problem with your home directory or something. Does anyone have any ideas??

---

### Post by ~LoKe on 2007-04-25
Here you are!
> loke@x04d:~$ ls ~/.mozilla/firefox/
n27apa6t.default  pluginreg.dat  profiles.ini

---

### Post by ~LoKe on 2007-04-25
Deleting my profile fixed the Firefox problem.  Not sure why I didn't try until now.

I imagine ET is just the same. =]

**EDIT:** delete etconfig.cfg and that's all good and well now, too!

Thanks!

---

