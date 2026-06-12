---
title: "RSYNC CRC check problem!!!  please help!!!"
date: 2013-06-27
forum: General Help
---

### Post by DrAlbert on 2013-06-27
Hi consider this situation:
you have a large filesystem and want to do a backup. normally you don't want to use rsync with CRC check because of many calculation that should be done because of CRC calculation. but with modification time and size option some files that didn't really changed are backuped again (I don't know why!)
is it possible to tell to rsync to first do a check for modification time and size and among those files(that rsync diagnosed as different in modification time or size) do a crc check?
thanks.

---

### Post by papibe on 2013-06-27
Hi DrAlbert.

Strictly no (no way to setup that logic), but that can be done in two passes.

If you run a dry run (--dry-run or -n) you can get the list of the files that were selected by the regular time and size algorithm. Then, you can take that list and run another rsync command, this time syncing using checksums.

This would be a simple example:
```
rsync -ain --out-format='%n' source/ destination/ | rsync -av -c --files-from=- source/ destination/
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by DrAlbert on 2013-07-04
thank a lot! it works very good. would you please tell me more about "-ain" option. I couldn't find this option in rsync man page or when google it.

---

### Post by papibe on 2013-07-04
Sure.

-ain is actually 3 options:
[LIST]
[*]-a is a short for **--archive**. It implies -rlptgoD (no -H,-A,-X). It's the most common option to sync directories.
[*]-i is a short for **--itemize-changes**. It allows to generate a list of the changes. In this case, of the potential changes.
[*]-n is a short for **--dry-run**. Which does not actually synchronize, but run through the current algorithm and print out the changes as if they were happening.
[/LIST]
In practice, -ain gets you a list of file and directories that rsync should sync, but without actually doing it.

Does that help?
Regards.

---

### Post by DrAlbert on 2013-07-05
I learned many things about linux in ubuntuforums and this was one of those. thank you!

---

