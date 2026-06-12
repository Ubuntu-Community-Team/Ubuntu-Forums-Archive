---
title: "Wget problem with local links"
date: 2007-11-06
forum: General Help
---

### Post by samjh on 2007-11-06
I've been trying to archive the very useful [www.cplusplus.com](www.cplusplus.com) website using wget, for local browsing.

The problem is none of the links downloaded by wget work.

This is the command I used:
```
wget -r -k -p --level=4 http://www.cplusplus.com/
```

After download has finished, let's say I open up the home index.html page at: ~/docs/www.cplusplus.com/index.html

Works fine.

But if I click on any of the links, they end up pointing to: file:///*whateverfile*.html

Upon examining the source code of each of the downloaded files, I find that every reference to other files begin with a "/", causing the browser to look for that file starting from the root directory of the file system, rather than the root directory of the archive.

Can anyone help?

---

### Post by K.Mandla on 2007-11-06
Moved to General Help.

---

### Post by mahousaru on 2007-11-06
For archiving sites I find httrack to be the best tool.

---

