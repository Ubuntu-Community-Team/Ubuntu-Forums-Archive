---
title: "extract individual tiny file from huge tar"
date: 2008-06-17
forum: General Help
---

### Post by watricky on 2008-06-17
I've been going through the documentation on tar trying to figure out if there's a way from commandline to specifically extract an individual file from a tarball without having to extract everything.

I happen to be working with huge tarballs (upwards of 5GB each) and often I need only to extract a small file (< 50KB) from the huge tarball.

This can take quite a few minutes to extract everything and it seems to be a waste of time and (temporarily) disk space considering that I don't need most of the resulting extracted data.

---

### Post by sdennie on 2008-06-17
This is actually much easier than it seems:

```

tar xvf whatever.tar path/to/file/in/tar

```

It's still going to be a slow operation on large tar files but, you won't need to extract the whole file.

---

### Post by watricky on 2008-06-18
Lol. Much simpler than I thought it would be.

Thanks. :)

---

### Post by sdennie on 2008-06-18
Glad to help.  A quick skim of the manpage doesn't make it really obvious that syntax like that will work on extraction.  One nice thing about the gnu tar is that the same command will work on a .tar.gz or .tar.bz2 so, you can just as easily pull a file out of a compressed tarball (though, it will be slower).

---

