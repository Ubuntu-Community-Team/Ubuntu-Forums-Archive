---
title: "how can i use find to locate files with characters in certain places?"
date: 2008-02-04
forum: General Help
---

### Post by narehart on 2008-02-04
I've googled this and read through the man pages and maybe I'm an idiot but I just don't get it.  How can I use the find command to search for files that have a certain character in a certain place in their name?

For, example I want to find all the files in my /home directory that have an a in the second place of their name.  How would I do that?

---

### Post by Gerard Barberi on 2008-02-04
Not sure.  Try using [wildcards.]("http://www.tuxfiles.org/linuxhelp/wildcards.html")

---

### Post by B'man on 2008-02-04
```
find -name "?a*"
```

See the link above.

---

### Post by narehart on 2008-02-11
thanks guys. i figured it out!

---

