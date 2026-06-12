---
title: "ntfs-3g cannot copy many files"
date: 2006-10-30
forum: General Help
---

### Post by shesha on 2006-10-30
I am trying to copy c:windows directory to another ntfs partition. But after copying some files it starts complaing "operation not permitted". Has any one know how to solve this?

mount looks as follows...
/dev/hda2 on /root/d type fuse (rw,nosuid,nodev,noatime,allow_other)

I am using simple cp -R command after mounting using ntfs-3g.

Any help is higly regarded.
Thanks.

---

### Post by lawina on 2006-10-30
According to the sourceforge website for ntfs-3g:

Problem:    "Operation not supported" message when creating a file:
 Answer:     This is a controlled refusal of file creation which can happen 
             when there are already about 100,000 files on the NTFS and the
             MFT needs to be extended in a way which isn't implemented yet.
 Workaround: Delete files then you can create new ones.
 Status:     High priority work.
 
 
 Problem:    "Operation not supported" message when deleting a file:
 Answer:     The support for certain very-very rare directory update 
             operations weren't fully tested yet, so they are not 
             included in the release. This is so rare that you probably
 	    will never see it ;-)
 Workaround: Delete or create other files in the same directory until you
 	    can remove the file you originally wanted.
 Status:     High priority work.

---

