---
title: "duplicity without history"
date: 2014-05-13
forum: General Help
---

### Post by contremaitre on 2014-05-13
Hi,

I'd like to backup some folders, encrypted, with rsync like algorithm.
I don't want to keep old files or history (so like with rsync --delete)
Duplicity looks like a good solution, but I don't know if it's possible to remove the history it keeps :
The incremental backup keeps every version of files, and the full backup makes a new copy of the whole folder.

Would there be a set of option to do what I need ?

Thanks.

---

### Post by contremaitre on 2014-05-26
I found rsyncrypto

---

