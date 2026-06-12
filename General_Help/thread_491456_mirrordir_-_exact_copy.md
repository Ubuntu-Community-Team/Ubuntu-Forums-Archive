---
title: "mirrordir - exact copy?"
date: 2007-07-03
forum: General Help
---

### Post by hove99 on 2007-07-03
I'm using mirrordir to backup my files to an FTP-server, and as the man file says:

"Mirrordir duplicates device/special files and file/directory access times exactly."

But when I try to mirror from local HDD to FTP, the access time and modification time of the file has changed. I have tried the options --access-time and --restore-access, but with no effect.

Does anyone have experience with mirrordir? Is this supposed to happen or is it a bug? How are the times preserved?

Thanx

---

### Post by jpeddicord on 2007-07-05
Try using rsync instead:

[http://en.wikipedia.org/wiki/Rsync](http://en.wikipedia.org/wiki/Rsync)

If you use it with the -t option, it syncs the times correctly. (You can also just use the --archive option to just mirror the directory exactly. Equivalent of -rlptgoD)

Jacob

---

### Post by hove99 on 2007-07-08
As far as I know, rsync doesn't work with FTP? I have tried to use mirrordir on local directories, and here the times are preserved. So it must be and FTP-thing...

---

