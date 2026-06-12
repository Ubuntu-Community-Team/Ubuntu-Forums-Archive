---
title: "how to remove multiple files ?"
date: 2013-12-04
forum: General Help
---

### Post by sanko50 on 2013-12-04
Hi,

I remove single file by this command

rm -r  directory



If I want to remove multiple file at one go ..what should be the command ?

rm -r  directory1 , directory2 , directory3 , directory4 ,....   //This does not work.

Whats the correct command to remove multiple file at one go ?


I  am using ubuntu 10 server edition.

---

### Post by drmrgd on 2013-12-04
You can do it without adding the commas between the directories you want to delete:

```

rm -r directory1 directory2 directory3

```

You might also find it easier to do things like globbing (let's assume you want to remove anything called directory#):

```

rm -r directory*

```

Or if you want to remove a subset (let's say you wanted to remove directory2 - directory4 without removing the rest):

```

rm -r directory{2..4}

```

There are several other tricks you can pull depending on directory names.  The short answer, though, is to just not add the commas when you're trying to delete multiple directories :)

---

### Post by oldos2er on 2013-12-04
Please wait a *minimum* of 24 hours before bumping your post, we have members from all over the world and it takes time for them all to see your post.

---

