---
title: "tar extracting with symlinks"
date: 2007-05-09
forum: General Help
---

### Post by woland on 2007-05-09
I'm trying to make an embedded system to work.
I've made a backup in tar.gz form on the whole flash disk.
Unfortunately, I've screwed up and I need to recover from that  backup.
The problem is that tar wouldn't recreate symlinks and returns an error message.

How do I make tar to extract everything on the archive?
The file system is ext3.

---

### Post by mlind on 2007-05-09
Are symlinks present in the archive? Tar should preserve symlinks by default.
If you make backup that contains special files like device nodes or similar, use cpio instead.

---

### Post by woland on 2007-05-09
The destination device (the one I need to restore) is formatted. So there shouldn't be any symlinks.

I'll use cpio next time, however, is it possible to rescue that partition from this backup?
It was a root partition of a Debian for ARM processors.

---

### Post by mlind on 2007-05-09
> **woland said:**
> The destination device (the one I need to restore) is formatted. So there shouldn't be any symlinks.

I'll use cpio next time, however, is it possible to rescue that partition from this backup?
It was a root partition of a Debian for ARM processors.

What's the output before tar dies?

---

### Post by woland on 2007-05-09
It was "Cannot create symlink in.. file doesn't not exist"
And a the end "tar: Error exit delayed from previous errors"

I can see the first message only if I use the GUI. If I use the the command line, I only get the last message.

EDIT: I used the following command: sudo tar -xvzf /path/to/file.tar.gz

---

### Post by mlind on 2007-05-09
If you could find out the problematic file from tar output or using ztf (list archive contents), then you could skip this file/symlink by using --exclude option

---

