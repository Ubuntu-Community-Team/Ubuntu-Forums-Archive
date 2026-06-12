---
title: "Firefox - How to backup bookmarks from command line"
date: 2013-11-21
forum: General Help
---

### Post by frogwarrior on 2013-11-21
I wanna make a shell script to back up various things automatically, so I need to know how to backup firefox bookmarks from the command line. Is there a simple way to do this?

---

### Post by vasa1 on 2013-11-21
```
[05:06 PM] ~ $ ls /home/vasa1/.mozilla/firefox/w4wcp85s.default/bookmarkbackups
bookmarks-2013-11-11_28.json  bookmarks-2013-11-14_32.json  bookmarks-2013-11-17_29.json  bookmarks-2013-11-20_29.json
bookmarks-2013-11-12_28.json  bookmarks-2013-11-15_35.json  bookmarks-2013-11-18_28.json  bookmarks-2013-11-21_29.json
bookmarks-2013-11-13_28.json  bookmarks-2013-11-16_36.json  bookmarks-2013-11-19_28.json
[05:06 PM] ~ $ 

```
The .json files are plain text.

---

### Post by philinux on 2013-11-21
As vasa1 points out they are all in the bookmarkbackups folder so your script could just copy (cp command) that folder to wherever you backups are stored.

---

### Post by frogwarrior on 2013-11-22
Thanks!

---

### Post by sgage on 2013-11-23
> **frogwarrior said:**
> Thanks!

Be advised that the afore-mentioned json files do not contain the favicons of visited sites, nor browsing history. For that you want to back up places.sqlite (in the main profile directory).

---

