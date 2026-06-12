---
title: "firefox bookmarks disappear"
date: 2005-05-01
forum: General Help
---

### Post by bennettg on 2005-05-01
nOOb here......

after loading ubuntu, i couldnt import my ff bookmarks from my xp dual boot.  so i manually copied them into /etc/mozilla-firefox.  

i can add/delete bookmarks, but upon restart all my changes disappear.  i even deleted the bookmarks.html file in /etc/mozilla-firefox without success.

any ideas?

---

### Post by Eproxus on 2005-05-03
Did the exact same thing and got the same problem. It's due to the file permissions.

This is what I did, should work for you too:
```
cd ~/.mozilla/firefox/default.flo/
chmod 644 bookmarks.*
```

This gives you read and write permissions as a owner, and others can read the files.

Hope it helps!

---

