---
title: "how would you select all files that contain a word/phrase?"
date: 2012-11-17
forum: General Help
---

### Post by fuzzylogic25 on 2012-11-17
I think this is done using grep command but I dont know how.

Basically in a folder, there are 1000s of files. I want to move all files in that folder that contain the word "cat" or some phrase like "hello cat" to another folder.

How can we do this?

THanks!

---

### Post by kc1di on 2012-11-17
Hi fuzzylogic25,

Here is a link with a little tutorial on the use of the grep command
it may be helpful to you.
[http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/]("http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/")

---

### Post by Impavidus on 2012-11-17
Use a loop, if, grep and mv.
```
for file in *
do
if grep -q 'hello cat' "$file"
then
mv "$file" newdir/
fi
done
```will do the trick. It is advisable to do a "dry run" first by putting echo in front of mv, so it will show you what the command will do. Also make sure your new directory exists. If you forget and omit the trailing slash you will rename all matching files to the same name, destroying them (yes, a few days ago someone on this forum told he made that mistake).

---

### Post by dragonfly41 on 2012-11-17
See package Recoll in Software Centre

---

### Post by Vaphell on 2012-11-17
```
for file in [COLOR="Red"]`ls`[/COLOR]
do
if grep -q 'hello cat' [COLOR="Red"]$file[/COLOR]
then
mv [COLOR="Red"]$file[/COLOR] newdir/
fi
done
```

this is bad, you don't need to embed ls to get the list of files.
*for file in *;...* will do
also always quote variables to prevent breaking up on whitespace chars ("$file")



one could also go with something like this ( make grep print out the list and iterate over that list in a loop)
```
while IFS= read -rd $'\0' f; do echo mv "$f" /dest/dir/; done < <( grep -lZ 'hello cat' * )
```

---

### Post by Impavidus on 2012-11-17
OK, you're right. I'll fix it. I never use file names with spaces, so I forgot about that.

---

