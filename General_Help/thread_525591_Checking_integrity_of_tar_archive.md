---
title: "Checking integrity of tar archive"
date: 2007-08-14
forum: General Help
---

### Post by Ozor Mox on 2007-08-14
I was wondering...does either running -t (to list files in an archive) or -d (to compare differences between archive and file system) verify the integrity of a tar archive (gzipped or not), or is the only true way to verify it to actually extract it?

This is for the purposes of making sure a backup of important data could actually be restored if required.

---

### Post by Ozor Mox on 2007-08-14
Oh and one other thing... Does a standard tar archive as used in the example on the man page (tar -cvvf foo.tar foo/) preserve everything that needs preserving (ownerships, permissions, timestamps and so on) or is the p option required? If you tar using the archive manager instead, does this preserve everything automatically?

---

