---
title: "Problem with slbackup-php"
date: 2007-12-22
forum: General Help
---

### Post by giuffsalvo on 2007-12-22
Hi, I've installed slbackup and slbackup-php, the web frontend to the former. I set up Apache2 to use SSL on [https://localhost/slbackup-php](https://localhost/slbackup-php), and up to this point everything is fine.
The problem is that the php page of slbackup (index.php) asks me the root password, because apparently it needs it to work on the filesystem, but when I insert it and click on 'Login', I'm not anyway able to use the various functions of the frontend (I activated the root account, just for this reason, otherwise I'd put an ! at the beginning of the root password on /etc/shadow). It keeps asking me this password!
What could be the problem? I've also tried to look at the source code of index.php, but it's too much complicated for me (so far...).
Thanks to anyone who will help me

---

### Post by samosamo on 2008-05-26
bumping this, i have the same issue.

---

