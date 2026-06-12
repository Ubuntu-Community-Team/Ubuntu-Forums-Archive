---
title: "can't delete folder"
date: 2013-01-22
forum: General Help
---

### Post by lightsaberlesbian on 2013-01-22
I'm encountering a weird issue with removing a folder

When I try to delete it I get "Could not rename file..."

Strangely there's another similarly folder placed elsewhere that gives me the same error.

I currently run Kubuntu 12.04.  Any ideas?

---

### Post by llamabr on 2013-01-22
copy/paste what you type and the output.  Use the # tabs for code.

Also, from command line do:

```
ls -lh filename
```

and post the output

---

### Post by lightsaberlesbian on 2013-01-24
here ya go

> ls -lh "to read"
total 0
drwx------ 1 sushi sushi 0 Jan 22 20:02 Margaret Atwood - The Blind Assassin


---

### Post by Bashing-om on 2013-01-24
From your output I see three possibilities:
1. Only the owner of the file may access it (sushi)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
2. The file name has spaces in it. In linux a space is a delimiter, thus if not escaped a line command sees "Margaret Atwood - The Blind Assassin" as 4 separate arguments: Margaret, Atwood-The, Blind, and Assassin.
3. Linux is case sensitive; Margaret and margaret are two different files, If you reference Margaret as margaret, then Margaret will not be found.
-----------
my file linux way -> my_file or maybe like my-file/Avoid spaces in file names, keeps things simpler//
[INDENT][INDENT]hth
 
[/INDENT][/INDENT]

---

