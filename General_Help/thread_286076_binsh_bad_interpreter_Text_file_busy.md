---
title: "/bin/sh: bad interpreter: Text file busy"
date: 2006-10-27
forum: General Help
---

### Post by robbbert on 2006-10-27
Hi!
Just upgraded from Dapper to Edgy. No errors so far *thanks* but this one:
```
$ /path/to/file.bin'
bash: /path/to/file.bin: /bin/sh: bad interpreter: Text file busy
```
Tried that by using sudo, too, same result.
Recreated the symlink by
```
ln -s /bin/dash /bin/sh
```
but it didn't help.
Executing /bin/bash /path/to/file.bin, directly, works.
Other symlinks do work.

Any ideas?
Thanks Robert

--------------------------------------------
Edit: Works now, after a reboot - at least in parts: Double-clicking in Nautilus does not do anything (I've set it up to "run executable files when they are clicked") but executing bin files in the terminal now works.
BTW, there'd been a reboot after the upgrade, and before the error occured.
Thanks

---

