---
title: "I shift-deleted Documents..."
date: 2008-03-22
forum: General Help
---

### Post by NCLI on 2008-03-22
Yes, I was that stupid. It happened by accident while cleaning up my Home folder...

I know that there are a lot of programs for restoring lost files on an NTFS file system, but are there any for ext3?

---

### Post by Thanoulis on 2008-03-22
You cannot undelete/recover files from the ext3 filesystem...:( You can in ext2 though...

Here is what Andreas Linger (one of the developers) said about:

> In order to ensure that ext3 can safely resume an unlink after a crash, it actually zeros out the block pointers in the inode, whereas
ext2 just marks these blocks as unused in the block bitmaps and marks the inode as "deleted" and leaves the block pointers alone.

Your only hope is to grep for strings (if it was a text file) with something like that:

```
grep --binary-files=text -30 "<\%" /dev/hda6 >output
```

---

### Post by hyperair on 2008-03-22
Try this program called photorec from the repository. It's found in the "testdisk" package. It works best with photos, but I recovered some of my documents using this as well. MP3s are completely shredded apart though. A 5 minutes mp3 may become many 5-second mp3s.

---

### Post by NCLI on 2008-03-22
Thanks, but I was working with odf spreadsheets, and all I got out of the recovery process is a lot of txt files.

Any way to remake the odf files from these fragments?

---

