---
title: "gvfsd-http What does this actually do?"
date: 2012-11-27
forum: General Help
---

### Post by cryptotheslow on 2012-11-27
As per title really: what is gvfsd-http and what does it do?

I noticed it recently in my process list as:
/usr/lib/gvfs/gvfsd-http --spawner :1.6 /org/gtk/gvfs/exec_spaw/2

with various outbound connections.

My search-fu must be lacking as all I find is discussions similar to this asking what it is and the most complete answers simply saying it is part of gvfs so best not to remove it. That doesn't leave a good feeling with me for a process that is making outbound connections.

Anyone have any information which package this belongs to at least?

Thanks :)

---

### Post by StinkySQL on 2012-11-27
Gnome Virtual File System Daemon - part of the file system and your GUI. You may have your package manager reporting your usage (system|Admin|update manager|settings tab), or some other program updating lots of files. Check out this thread.

[http://ubuntuforums.org/showthread.php?t=981606](http://ubuntuforums.org/showthread.php?t=981606)

---

### Post by cryptotheslow on 2012-11-28
Thanks for the reply.

That statistics setting in update manager is unchecked and rhythmbox (or any other media app) isn't running.

Quite weird.

---

