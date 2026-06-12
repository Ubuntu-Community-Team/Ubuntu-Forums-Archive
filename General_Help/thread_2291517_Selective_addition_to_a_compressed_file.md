---
title: "Selective addition to a compressed file?"
date: 2015-08-20
forum: General Help
---

### Post by Dr._B on 2015-08-20
I have a somewhat unusual problem and am hoping someone here knows how to address it. I have to submit some data that is part of a publication to a public repository. However, the data to submit is mixed into dozens of folders containing materials that are not to be submitted. While it is  easily find all of the relevant files, as they have a set of unique file extensions and thus show up in nautilus search, I also need to preserve the folder structure. I.E. I need to compress all of the files with a given extension directory and all of its  multiple levels of sub-directories, while preserving the folder structure and ignoring all other files.

I've tried to script this, and have failed dismally.

Can anyone help?

Thanks

Bryan

---

### Post by steeldriver on 2015-08-20
[I] [stolen from this SO answer: [URL="http://serverfault.com/questions/113820/how-can-i-make-a-tar-of-selective-file-type-under-a-directory"]http://serverfault.com/questions/113820/how-can-i-make-a-tar-of-selective-file-type-under-a-directory ]
[/URL][/I]
You should be able to use a combination of `find` and `tar` with the `-T` option, I think

From `man tar`:
```

     -T, --files-from FILE
           get names to extract or create from FILE

```

e.g. at its most basic

```

find . -name '*.ext' | tar cvf myfiles.tar -T -

```

However probably better to use null terminators

```

     --null
           -T reads null-terminated names, disable -C

```

i.e.

```

find . -name '*.ext' -print0 | tar cvf myfiles.tar --null -T -

```

Compress the resulting tarball after, or add `z` or `j` to the tar  command and adjust the filename accordingly to compress (gzip / bz2)  on  the fly.

Another way to do it might be to use rsync with appropriate include/exclude filters.

---

