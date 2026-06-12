---
title: "script to rename multiple files"
date: 2006-10-10
forum: General Help
---

### Post by sup? on 2006-10-10
I have a directory with ~1000 mp3s in the format of "x - title.mp3" where x is a two digit number. I want to remove everything before the title name. Is there a way to do this in bash or perl/python? I was trying to modify an older perl script of mine to do this but I got absolutely nowehere due to my general lack of knowledge.
Any help would be appreciated.

---

### Post by mitch.c on 2006-10-10
> **sup? said:**
> I have a directory with ~1000 mp3s in the format of "x - title.mp3" where x is a two digit number. I want to remove everything before the title name. Is there a way to do this in bash or perl/python? I was trying to modify an older perl script of mine to do this but I got absolutely nowehere due to my general lack of knowledge.
Any help would be appreciated.

There's a really great rename command that uses Perl regex. To change the names of files named with the pattern you specified, use:
```
rename 's/^[0-9]{2} - //' *.mp3
```

---

### Post by sup? on 2006-10-10
mitch.c, thank you very much.
I might quickly add that this has to be the reason I love ubuntu so much. Friendly people, good help in a timely manner, and no rtfm replies.
Cheers

---

### Post by beerorkid on 2006-10-10
I use mvb, it is pretty nice
[http://ubuntuguide.org/wiki/Dapper#How_to_rename_all_files_in_directory_at_once](http://ubuntuguide.org/wiki/Dapper#How_to_rename_all_files_in_directory_at_once)

---

### Post by argie on 2006-10-10
I just looked in Applications > System Tools and I have a "Bulk Rename" tool which seems to have a nice interface. haven't tried it yet though.

ThunarBulkRename it's called, comes with thunar perhaps? :)

---

### Post by mitch.c on 2006-10-10
Funny, I didn't realize that the 'rename' command I've been using (and recommended in my original reply) is a symlink to 'prename' which is actually part of the Perl package. It's symlinked using the 'rename' alternative, so the rename program selected on your system may be symlinked to something else.

You can check by doing:
```
update-alternatives --display rename
```

---

### Post by Georges on 2006-12-04
there is also the package renameutils

and there is mmv which is what I use often.

Still, rename (prename) sounds like a great tool.

---

