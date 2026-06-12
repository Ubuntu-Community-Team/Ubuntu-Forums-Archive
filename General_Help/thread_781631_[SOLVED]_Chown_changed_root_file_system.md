---
title: "[SOLVED] Chown changed root file system"
date: 2008-05-04
forum: General Help
---

### Post by Super TWiT on 2008-05-04
when I chowned a home directory to import my old files, there was a symlink that linked to /usr/share/examples.  I guess chown followed it.  Anyway, now I am able to add files on /.  I am also able to delete all symlinks on /.  However, I can't do anything to files in folders.  The weirdest part was, when I ran chown, I set it to recursive mode.  If I messed something up, it would have messed up everything.  I wasn't even in that directory when I ran chown.  I think this may be a bug.  However, I probably missed something obvious.  Is this normal?  I don't think this happened in gutsy.

---

### Post by Zorael on 2008-05-04
Well, you could chown everything back to root and then just fix your home folder.

---

### Post by Super TWiT on 2008-05-09
Weird, I updated my system and that fixed it.  I guess problem solved.  Thanks for replying to my thread.

---

