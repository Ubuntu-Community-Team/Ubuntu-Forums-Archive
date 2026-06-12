---
title: "Backing Up"
date: 2007-03-01
forum: General Help
---

### Post by Megaqwerty on 2007-03-01
Hello all, I'm having a problem when trying to backup my system to a windows share, (I'm doing this all in the CLI.) I mounted the share fine, and ran tar to bzip my filesystem (some directories excluded) to this mounted windows share. It works well for a while, but then something weird happens:
```
 bzip2: I/O or other error, bailing out.  Possible reason follows.
bzip2: Input/output error
        Input file = (stdin), output file = (stdout) 
```

This happens every time I attempt it, and I get a very similar message when attempting to do it with gzip as well. The mounted share is now (after I get the error) inaccessible, and locks up whatever program I try to open it with (even 'cd'.) It then is accessible only after a reboot.

Any help would be appreciated,

Megaqwerty

EDIT: smbiod is now after my most recent attempt taking up at least 89% of my cpu, and I can't kill it. The command executes, but the program stays alive...

---

### Post by Megaqwerty on 2007-03-02
Bump.

---

