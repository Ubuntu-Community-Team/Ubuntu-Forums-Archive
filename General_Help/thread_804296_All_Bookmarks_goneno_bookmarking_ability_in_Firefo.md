---
title: "All Bookmarks gone/no bookmarking ability in Firefox"
date: 2008-05-23
forum: General Help
---

### Post by Nelfstar on 2008-05-23
So my problem started when I entered
 ```
aoss firefox
```

And now when I start firefox all my Bookmarks are gone, and I have no ability to bookmark.

Any help would be appreciated.

Thank you in advance.

---

### Post by Nelfstar on 2008-05-23
bump

---

### Post by Steve413z on 2008-05-23
you should probably be able to recover your bookmarks at least:

~/.mozilla/firefox/___RANDOM_LETTERS___.default/bookmarks.html

or this folder:
~/.mozilla/firefox/___RANDOM_LETTERS___.default/bookmarkbackups/


you might need to create a new firefox profile

---

### Post by Bubba64 on 2008-05-23
> **Nelfstar said:**
> So my problem started when I entered
 ```
aoss firefox
```

And now when I start firefox all my Bookmarks are gone, and I have no ability to bookmark.

Any help would be appreciated.

Thank you in advance.

Go to Mozilla in home they should be there still you will have to look around but there are bookmark backup files in there.

---

### Post by MrEps on 2008-09-24
A little late, but I got the same problem, and solved it.

If went to this folder in a terminal window:

~/.mozilla/firefox/___RANDOM_LETTERS___.default/

then I typed:

```
sudo chown <user>:<user> *.*
```

replace <user> with your default user name, and restart firefox. Worked for me.

---

