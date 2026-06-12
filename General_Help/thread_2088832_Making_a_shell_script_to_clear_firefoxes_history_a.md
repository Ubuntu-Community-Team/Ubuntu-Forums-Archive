---
title: "Making a shell script to clear firefoxes history and cookies for you"
date: 2012-11-27
forum: General Help
---

### Post by alkal0id on 2012-11-27
I googled it and found one tutorial but it must be outdated because they say to use the following code:
```
rm .mozilla/firefox/user.default/Cache/*
rm .mozilla/firefox/user.default/cookies.txt
rm .mozilla/firefox/user.default/history.dat
rm .mozilla/firefox/user.default/downloads.rdf
```

but none of those files actually exist in my directory. The Cache folder exists but there doesn't seem to be much in it. How do you do this in modern versions of firefox?

---

### Post by LuisGMarine on 2012-11-27
Cookies:
You need to remove the "cookies.sqlite" file.
[http://kb.mozillazine.org/Cookies]("http://kb.mozillazine.org/Cookies")

... and I think for the rest these might better help you out.  Good luck.

[kb.mozillazine.org/Profile_folder_-_Firefox#Files]("kb.mozillazine.org/Profile_folder_-_Firefox#Files")

---

### Post by CharlesA on 2012-11-27
Wouldn't it be easier to just set firefox to clear those things when you close it?

---

### Post by Vaphell on 2012-11-27
or browse in private mode all the time?

---

