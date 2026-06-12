---
title: "Recover Firefox bookmarks from second drive"
date: 2021-12-24
forum: General Help
---

### Post by jackbn on 2021-12-24
My former primary Ubuntu drive no longer boots. I have this drive now set as secondary, but need to recover my Firefox bookmarks from the former primary. How? 
My last bookmark backup was before recent activity, and I believe the recent bookmarks must still be on the former primary drive, somewhere.

---

### Post by oldfred on 2021-12-24
I typically use same profile for both Firefox & Thunderbird which is a hidden file.
There also is a bookmarks backup in the profile.
It should be like this which is mine, you have unique user & 8 char as profile:
/home/fred/.mozilla/firefox/knd9g8er.default-release

[https://support.mozilla.org/en-US/products/firefox](https://support.mozilla.org/en-US/products/firefox)
Profiles - Where Firefox stores your bookmarks, passwords and other user data
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles](https://support.mozilla.org/en-US/kb/back-and-restore-information-firefox-profiles)

---

### Post by Holger_Gehrke on 2021-12-24
In your old home directory should be a directory '.mozilla/firefox/*.default'. There is a sqlite database named 'places.sqlite' in there. You bookmarks are inside in a table named moz_bookmarks. The URLs for the bookmarks are not in that table but in the table 'moz_places' and there's a connection between those tables - the values in the fields moz_bookmarks.fk and moz_places.id. A query that should get all the titles and URLs would look something like this:
```

select moz_bookmarks.title,moz_places.url from moz_bookmarks, moz_places where moz_places.id=moz_bookmarks.fk;

```

Holger

---

### Post by ajgreeny on 2021-12-24
There will also be some bookmark backups in a folder called ***.mozilla/firefox/x#x#x#x.default/bookmarkbackups*** all being .jsonlz4 files which can be imported directly using the bookmarks manager in FF.

---

