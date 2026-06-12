---
title: "Programmatically delete files in Bash recursively based on file name."
date: 2007-03-09
forum: General Help
---

### Post by Dygear on 2007-03-09
I'm looking for a way to delete files in BASH based on file name.

Basically, I've imported (FTP'ed) the My Music folder from my windows desktop on to my ubuntu laptop. And the FTP includes the Desktop.ini file and all of the Magic files (Names that include {ABCDEFG-1234567890-HIJKLMNOP-1234567890-QRSTUVWXYZ}.ext like that) I'd like to delete them. Any clue how to do that file BASH?

Thanks for ANY help.

---

### Post by tribble222 on 2007-03-09
If your music folder is /home/dygear/music and you want to remove any file in it that contains .ini then you'd run

rm -r /home/dygear/music/*.ini

---

### Post by vinchi007 on 2007-03-12
do first "ls -l *.ini" and see if you do not have any other ini files that you do not want to remove, then as a precaution you can use statement as mentioned above, but adding "-i" to remove command, which will prompt you with file name you want deleted:
"rm -ir *.ini"

---

### Post by tlacuache on 2007-03-12
Another good way to do it is to use find with the "exec" parameter.

First get the "find" statement which returns the files you want:

```
find -iname *.txt
```

for example would list all files that match the wildcard pattern *.txt. You could skip straight to the next step, but I always like to run the "find" without the exec parameter first to make sure I'm really going to be deleting what I say I am.

Then, to delete those files:

```
find -iname *.txt -exec rm {} \;
```

This means "find all files ending in .txt, and execute the command rm on each file." If you were really paranoid you could add -i after the rm so it would ask you to confirm each file deleted.

---

