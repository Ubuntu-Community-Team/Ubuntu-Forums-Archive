---
title: "simple ln question?"
date: 2008-06-09
forum: General Help
---

### Post by virgil_disgr4ce on 2008-06-09
Hi all, I'm trying to set up WebDAV on my Apache2 server.  I'm trying to make symbolic links to my mods-enabled dir:

sudo ln -s ../mods-available/dav*

but I keep getting this error:

ln: target `../mods-available/dav_lock.load' is not a directory

I see in the man page something about an error being returned if the last file is not a directory (this is the case) but I don't understand why or what to do about it... I don't want to "force removal" of any files; I don't want to remove any files at all, so I'm not sure what the manual is talking about.  Thanks for helping me out!

--Ted

---

### Post by Yellow Pasque on 2008-06-09
Are you trying to link an entire directory? Can you be a bit more specific, i.e. what do you want to create a link to and where do you want to create it?

---

### Post by virgil_disgr4ce on 2008-06-12
the ln -s ../mods-available/dav* command was part of some specific instructions I was following to set up WebDAV, basically just making links for each of 4 files.  No directories involved, which is why the manual notes are confusing.

So to reiterate, I was merely trying to make links for each of 4 files (that begin with dav),  into the current working directory.  I just did each individually and it worked fine, but I still want to understand why using dav* didn't work.

---

### Post by bingoUV on 2008-06-12
ln does not work like that. There are 3 main modes you can use ln in : 
1. One filepath argument. 
```

ln /path/to/target/file

```

This will make a link to /path/to/target/file in the current direcrory.

2. 2 filepath arguments 
```

ln /path/to/target/file /path/to/source/file

```

Now, /path/to/source/file is a link to /path/to/target/file

3. More than 2 arguments : the last argument **must** be a directory. 
```

ln /path/to/file/1 /path/to/file/2 /path/to/file/3 /path/to/file/4 /path/to/target/directory

```
This will make links to the previous argument paths in the target directory.

So there is no way you can use more than 2 arguments and last argument not be a directory. Note that dav* will expand to 4 different paths if there are 4 files that match the regular expression

---

### Post by virgil_disgr4ce on 2008-06-12
Oh I see, so since dav* IS expanding it out as I would have expected, it's just that the way ln's parameters work it's always expecting the last parameter to be the TARGET if there are more than 2.  I got you... I wish the man page was clearer :p

Thanks for taking the time to respond!  I had thought that dav* wasn't the right way to expand or something... at least that's right in principle ;)

---

