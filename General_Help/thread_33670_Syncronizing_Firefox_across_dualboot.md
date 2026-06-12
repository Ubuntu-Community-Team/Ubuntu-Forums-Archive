---
title: "Syncronizing Firefox across dualboot"
date: 2005-05-11
forum: General Help
---

### Post by chryz on 2005-05-11
Anyone know of a way to syncronize bookmarks on machine running dualboot - in other words making the bookmarks the same no matter if I'm using Windows or Ubuntu. Any ideas? ... works copying the files manually and tried making a link, but the get unlinked and replaced by Firefox.

---

### Post by James Wilford on 2005-05-11
[QUOTE=chryz]Anyone know of a way to syncronize bookmarks on machine running dualboot - in other words making the bookmarks the same no matter if I'm using Windows or Ubuntu. Any ideas? ... works copying the files manually and tried making a link, but the get unlinked and replaced by Firefox.[/QUOTE]
 [https://do-not-add.mozilla.org/extensions/moreinfo.php?application=firefox&category=Bookmarks&numpg=10&id=14](https://do-not-add.mozilla.org/extensions/moreinfo.php?application=firefox&category=Bookmarks&numpg=10&id=14)

---

### Post by chryz on 2005-05-11
[QUOTE=James Wilford][https://do-not-add.mozilla.org/extensions/moreinfo.php?application=firefox&category=Bookmarks&numpg=10&id=14](https://do-not-add.mozilla.org/extensions/moreinfo.php?application=firefox&category=Bookmarks&numpg=10&id=14)[/QUOTE]

That plugin doesn't work for, and won't install on the newer versions of Mozilla Firefox. Other than that it seems a bit overkill.

---

### Post by derrick1985 on 2005-05-11
[QUOTE=chryz]That plugin doesn't work for, and won't install on the newer versions of Mozilla Firefox. Other than that it seems a bit overkill.[/QUOTE]

You might be able to edit the Firefox .bin file and give a location for the bookmark (i don't know where exactly, check out mozilla's site for that one)

Also, don't forget, ubuntu cannot write to an NTFS partition, and windows can't write to an ext3 partition, so if you are going to store these anywheres, it will have to be on a fat32 partition.

---

