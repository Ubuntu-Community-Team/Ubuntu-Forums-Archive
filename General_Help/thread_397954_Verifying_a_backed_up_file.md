---
title: "Verifying a backed up file"
date: 2007-03-31
forum: General Help
---

### Post by Man_Beach on 2007-03-31
I've just created an archive of some important files and burnt it to a CD.

How can I compare the archive I made and the burnt copy of it, to make sure that they are identical and that there are no errors with the copy on the CD?

---

### Post by acormack on 2007-03-31
the only way i know is to decompress from the cd then use **diff** to compare

---

### Post by Man_Beach on 2007-04-01
I'm not sure that diff is quite the right thing. What I'm looking for (I think) is something like the old MS-DOS copy verify switch (copy /v) which verifies that there are no errors in the copy. [And it's many years since I've used anything like that!]

---

### Post by acormack on 2007-04-01
I guess it depends just how important the backup is to you.

It is always possible that the cp command thiks it worked.  What I recommended is a full test.

Remember you can use diff -r to recursively check whole directory trees

---

### Post by sunset_studies on 2007-04-01
If you don't mind using the terminal, you can use the md5sum command, e.g.:

md5sum path_to_archive_on_hard_drive

md5sum path_to_archive_on_cd

If the two results are the same, it's safe to assume the files are identical.

---

### Post by Man_Beach on 2007-04-01
Thank you sunset_studies. md5sum looks like it should do the trick.

---

