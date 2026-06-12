---
title: "Rename files, folders and strings"
date: 2007-02-09
forum: General Help
---

### Post by d-E-a-D on 2007-02-09
Hi, does anyone know if there is a program for unix (or not) that rename multiple files, multiple folders and strings in files recursively?

For example: I want to change all files, folders and strings in files that contain the word "images" to "imagens" all in the folder "loja".

RPL it's great to change strings with just "rpl -R images imagens loja/", but it does not change filenames and folders...
Or does anyone know if there is some software just like RPL but to rename files and folders recursively?

Thanks!!

---

### Post by jongkind on 2007-02-09
Sure:
[http://ubuntuguide.org/wiki/Dapper#How_to_rename_all_files_in_directory_at_once]("http://ubuntuguide.org/wiki/Dapper#How_to_rename_all_files_in_directory_at_once")

---

### Post by d-E-a-D on 2007-02-09
Thanks but that's not what i want, i said:

> **d-E-a-D said:**
> 
For example: I want to change all files, folders and strings in files that contain the word "images" to "imagens" all in the folder "loja".

RPL it's great to change strings with just "rpl -R images imagens loja/", but it does not change filenames and folders...
Or does anyone know if there is some software just like RPL but to rename files and folders recursively?


Please, first read and then answer !

Thanks

---

### Post by jongkind on 2007-02-09
You're welcome

---

### Post by stylishpants on 2007-02-09
If you have the 'perl' package installed, then you have the 'prename' utility (may also be called just 'rename'.)  This is a very simple file renamer.  It uses regular expressions and perl's "s///" operator to do renaming.  You can get a detailed description of regular expressions in the perl docs ("perldoc perlre" on the command line), but for your example simple strings will work fine.

```

fhanson@fhanson:/tmp$ rename --help
Unknown option: help
Usage: rename [-v] [-n] [-f] perlexpr [filenames]
```

To rename all files in a single directory, you would do this:

```

rename 's/images/imagens/' loja/*

```

To apply it to all files and folders within an entire directory subtree, one of the ways Unix allows you to do this is with the 'find' utility:

```
find loja/ -exec rename 's/images/imagens/' {} \;
```

If you want to change strings within the files too, that is a separate operation.  You already know how to use rpl, you can wrap it in a 'find' command as well.

Read the man page for 'find' for more details.

---

