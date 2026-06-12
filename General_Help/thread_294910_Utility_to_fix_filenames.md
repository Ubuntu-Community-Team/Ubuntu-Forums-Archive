---
title: "Utility to fix filenames?"
date: 2006-11-07
forum: General Help
---

### Post by dwasifar on 2006-11-07
I use Amarok with the collection housed on a network share.  Some of the filenames have extended characters.  If I mount the network share using iocharset=utf8,codepage=unicode,unicode in /etc/fstab, Amarok can't read the files correctly; but without that, the files show up wrong in Nautilus and won't copy correctly if I use a cp command in terminal.

My first idea was to mount the share twice, at two different mount points - once with the utf charset and once without.  But that won't work.  I know there is a utility or a script out there somewhere that will clean up these filenames, but I don't remember what it is.  Anyone?

---

### Post by Choad on 2006-11-07
there is an xfce tool called bulk rename that can rename music files based on the meta data found in them. 2 birds, 1 stone - the encoding will be nice and the whole collection will be named in the same fashion!

---

### Post by dwasifar on 2006-11-07
> **Choad said:**
> there is an xfce tool called bulk rename that can rename music files based on the meta data found in them. 2 birds, 1 stone - the encoding will be nice and the whole collection will be named in the same fashion!
What does it do with extended characters in the tags?  Do they make it into the filenames unchanged?

I really don't want to rename all the files based on the tags - I just want to fix this extended character problem.

---

### Post by Choad on 2006-11-07
it has a search + replace too

you could probably just search for a specific character that you want to remove, and then replace it with nothing :)

---

