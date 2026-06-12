---
title: "tar doesn't exclude hidden files"
date: 2005-08-08
forum: General Help
---

### Post by HJB on 2005-08-08
Hi.

What I want to do is make a backup of my home directory but exclude the hidden files

I have followed the instructions here: [http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087) which works well but when I add --exclude=/.* it doesn't exclude them.
Please show me the correct tar statement to backup a home directory and exclude the hidden files.

Bye
H

---

### Post by Sam on 2005-08-08
I'm not sure, but --exclude=/.* is not for excluding all hidden files in / ?

Maybe you should do --exclude=.*

---

### Post by frankos44 on 2007-12-18
Thats easy try:

tar czvf backup.tar.gz  ~/[a-zA-z]*  ~/.evolution

In the above example I excluded all hidden files except .evolution as I like to backup my emails.

---

