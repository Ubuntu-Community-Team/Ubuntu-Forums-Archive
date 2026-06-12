---
title: "firefox not upgrading..."
date: 2005-09-30
forum: General Help
---

### Post by kiwibird on 2005-09-30
I'm trying to upgrade mozilla-firefox and mozilla-firefox-gnome-support, and I keep getting this message:

```
E: /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
E: /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb:  trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
```

I've got 1.0.6 installed, and seemingly firefox and firefox-gnome-support (not mozilla-...), which won't go away... anyone have a clue what to do?

---

### Post by ltmon on 2005-09-30
I've got the same problem, so I marked firefox, firefox-gnome-support, mozilla-firefox and mozilla-firefox-gnome-support as held packages.

Only problem is now firefox doesn't work at all - it just doesn't start anything when I type "firefox" or "mozilla-firefox" at the command prompt.

Any help would be appreciated.

L.

EDIT: found this thread: [http://ubuntuforums.org/showthread.php?t=68733](http://ubuntuforums.org/showthread.php?t=68733)

---

### Post by kiwibird on 2005-09-30
Doodsie, I just managed to do the same thing, right before reading your post. Or, something which gave the same effect, at least. But thanks for the link, guess I should've searched. Doh.

---

