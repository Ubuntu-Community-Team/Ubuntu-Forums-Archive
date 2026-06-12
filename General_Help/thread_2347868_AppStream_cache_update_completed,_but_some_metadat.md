---
title: "AppStream cache update completed, but some metadata was ignored due to errors."
date: 2016-12-29
forum: General Help
---

### Post by vigilian on 2016-12-29
Hi,

even with the fix released and installed manually, I can't get rid of this message. 
"AppStream cache update completed, but some metadata was ignored due to errors."
it always happens when apt called after Réception de:20 [http://be.archive.ubuntu.com/ubuntu](http://be.archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]  -> DEP data files. never when it does only the normal way.
And it doesn't hang forever like described in the bug report.
Does anyone else have this problem ?

---

### Post by slickymaster on 2016-12-29
That's a known bug: [https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1575248](https://bugs.launchpad.net/ubuntu/+source/fwupd/+bug/1575248)

---

### Post by vigilian on 2016-12-29
answers is here 
[http://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d](http://askubuntu.com/questions/854168/how-i-can-fix-appstream-cache-update-completed-but-some-metadata-was-ignored-d)
version 0.10 of appstream in backport channel

and yet it was not satisfactory because nobody mentioned the backport update of appstream to 0.10 in place of originally 0.9.4.1 for the hanging bug resolved.

---

