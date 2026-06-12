---
title: "Firefox settings and bookmarks dissappeared"
date: 2005-05-24
forum: General Help
---

### Post by royg1234 on 2005-05-24
Hey.  My Firefox settings and bookmarks just dissappeared.  I think it has something to do with user profiles, but I don't remember exactly how I messed it up.  How do I restore it?

Thanks!

---

### Post by royg1234 on 2005-05-24
where is the info kept for bookmarks, extensions, themes, etc for each user?

---

### Post by Aidje on 2005-05-24
[QUOTE=royg1234]where is the info kept for bookmarks, extensions, themes, etc for each user?[/QUOTE]
 The profile folder is ~/.mozilla/firefox/xxxxxxxx.default/ (note that .mozilla is a hidden folder--it's still accessible though, even if you don't see it)

Some other useful folders are /usr/lib/mozilla-firefox/ and /etc/mozilla-firefox/ .

---

### Post by royg1234 on 2005-05-24
ah.  Thanks.  I'll take a look.

think what triggered this was I clicked on the Firefox launcher, and got impatient and clicked it again, and some dialog came up that said something about users.  I didn't really read it carefully, though, and just clicked an ok button that told the dialog to go ahead and create a new user profile I guess.  (there was an "exit" button, which I normally click on, but not this time).

---

### Post by royg1234 on 2005-05-25
Solution.  Apparently I created a new user profile, and Firefox just opened to it by default.  Evidence was in 

~/.mozilla/firefox/profiles.ini

```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=mvnk9dkj.default

[Profile1]
Name=Default Userhj
IsRelative=1
Path=pb44m5pt.Default Userhj
Default=1

``` 

I assumed that the new profile was added to the bottom, so I just moved "Default=1" to the top profile:

```

[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=mvnk9dkj.default
Default=1

[Profile1]
Name=Default Userhj
IsRelative=1
Path=pb44m5pt.Default Userhj

```

There's probably a menu for this somewhere in Firefox, but I couldn't find it, and this was easy enough.

---

