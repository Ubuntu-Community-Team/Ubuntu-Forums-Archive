---
title: "Compiler Errors: Conflicting Types, Previous Declaration"
date: 2007-12-16
forum: General Help
---

### Post by antisho on 2007-12-16
Please move if in the wrong place.

I am trying to compile something, and make gives me
```
../include/foo.h:41: error: conflicting types for `off_t'
/usr/include/sys/types.h:101: error: previous declaration of `off_t'
```
Googling gives some results, but I do not see anything immediately similar in the .c file. Any help?

---

### Post by cmnorton on 2007-12-16
Assuming that foo.h is your file, you've declared a type in foo.h that conflicts with what's in sys/types.h. That is usually not a good idea. 

Either rename l your type to something slightly different, so it means something to you or whoever reads your source code, or rely on the type declared in types.h.

---

### Post by antisho on 2007-12-16
So this was a source package I downloaded, I didn't write it, and there are a bunch of #includes so I don't know which one is conflicting.

---

### Post by geraldm on 2007-12-16
Your compiler needs code changes to compile successfully.  If you are not going to make the changes, then find a mailing list from the source, see if the problem has already been reported and corrected, or report the problem.  That is the best source, as others using that source may encounter the same problem.

Gerald

---

