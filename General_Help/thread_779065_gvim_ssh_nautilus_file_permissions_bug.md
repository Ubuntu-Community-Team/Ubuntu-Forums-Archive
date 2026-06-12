---
title: "gvim ssh nautilus file permissions bug"
date: 2008-05-02
forum: General Help
---

### Post by Apreche on 2008-05-02
So I have a server that I connect to via ssh through nautilus. The server has some files on it with permissions of 644.

If I ssh to the server on the command line and edit the files with vim, the permissions remain the same.

If I edit the files through nautilus over ssh with gedit, the permission remain untouched.

If I edit the files through nautilus over ssh with gvim, the permissions are changed to 600 the instant I hit save.

Any idea how to fix this?

---

### Post by Apreche on 2008-05-07
I did some further investigation of this bug, and I have filed a [bug report]("https://bugs.launchpad.net/ubuntu/+bug/227808").

---

