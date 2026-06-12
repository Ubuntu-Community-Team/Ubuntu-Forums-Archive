---
title: "UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY."
date: 2007-01-07
forum: General Help
---

### Post by janx on 2007-01-07
I have seen many posts about similar problems but I haven't been able to find a solution. It would be useful to get some advice about the options to give to fsck. I ran into this problem after a disk full situation which apparently left a file system with logical errors ("buffer I/O error on device...").

I am getting these error messages on a file system which is not '/', so it's not a problem to unmount it. When I run fsck without options, I get:
/dev/hda5: recovering journal
/dev/hda5 contains a file system with errors, check forced.

And then after numerous messages:
Force rewrite<y>?

Is it safe to answer <y> ?

What about 'fsck -cf'' ?

---

### Post by koenn on 2007-01-07
```
man fsck
```
will showw you all the options, and tell you that fsck is a front-end for other, filesystem-specific checkers, in you're case that might be ext3, so
```
man fsck.ext3
```

as to your question "is it save to answer yes ?" - i think that might depend on what the program said ***before*** it asks if you want to rewrite.
Even then, it may be hard to judge because these things are hard to interprete if you don't know how a filesystem is build (and I don't). On the other hand, it may be your only possible ***attempt ***to fix it .

I've "repaired" a couple of fs by just accepting the answer the program suggests - so far without loss of data - but that is no guarantee, of course.

---

### Post by janx on 2007-01-10
Thanks koenn, you were right. I managed to repair the fs answering the default to all questions (which is probably the same as: fsck -c). I have probably lost a few files though.

---

