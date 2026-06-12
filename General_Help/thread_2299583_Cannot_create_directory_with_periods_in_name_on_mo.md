---
title: "Cannot create directory with periods in name on mounted network share (cifs/nfs)"
date: 2015-10-19
forum: General Help
---

### Post by sblack55 on 2015-10-19
Forgive if this is answered somewhere - I cannot find it.

Having a problem creating directories that contain multiple embedded periods in the name on a mounted network share.  Same behavior with both nfs and cifs mounts to same share.  Windows boxes accessing the same share (a NAS, an oldish LG N2A2) have no problem.  And, of course, there is no problem on the internal file system.

I'm wondering if there are mount options that would help with this.  Of course, it just occurred to me that it could be a failure of support within the NAS box, which is a bit outdated.  I won't be able to test that until I get a newer one which will be a few months, at least.

Example directory: The Man from U.N.C.L.E.  (I need to experiment with shorter names and with single embedded periods.)

Ubuntu: Kodibuntu(Lubuntu) 14.04
mounting via fstab (a variety of options attempted with no changes in behavior)

---

### Post by TheFu on 2015-10-19
Do this from a terminal. Swap out the path for the real path on your NFS client system. Do not use root.

```
$ mkdir "/nfs/path/to/diretory/The Man from U.N.C.L.E."
```
using the same account.  What is the error? Please copy/paste the exact command and error(s) back here.

I can assure you that for Ubuntu and other full Linux servers, this is NOT an issue and nothing special is required.

---

### Post by sblack55 on 2015-10-19
Well, nevermind, dang it!  When I began to experiment I realized it was working after all.  A little more poking reveals the real problem is somehow tied to the way the creating program is working.  Turns out it doesn't even work in local folders.

---

### Post by TheFu on 2015-10-19
Please mark this thread as "solved" to help others avoid reading who would try to help. Save them some time.

---

