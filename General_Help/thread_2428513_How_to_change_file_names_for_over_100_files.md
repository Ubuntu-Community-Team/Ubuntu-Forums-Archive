---
title: "How to change file names for over 100 files?"
date: 2019-10-04
forum: General Help
---

### Post by robertcull1 on 2019-10-04
I have two questions that are similiar

--- question 1 ---

I have many files that are of the form

nnnn-nn-nn_nn.nn_00.txt

where n is a number from 0 to 9.

I would like to write a script to change the files to something like.

nnnn-nn-nn_nn.nn_string.txt

where "string" is just a character string.

--- question 2 ---

I also have over a hundred files that are of the form

nnnn-nn-nn_nn.nn_00_STRING.txt

Where "STRING" is just normal characters. I would like to change the filenames to something like

nnnn-nn-nn_nn.nn_new_STRING.txt

where "new" is just some characters.

Can someone please help?

---

### Post by Skaperen on 2019-10-04
man rename

---

### Post by TheFu on 2019-10-04
I would use rename.  This is a perl regex tool, so it has grouping and replacement if that's what you need.
Something like:
```
$ rename 's/_00.txt/_string.txt/g' *txt
```
is the simple answer. You can for searching at the beginning or end of strings using normal regex. 

For more complicated needs, often I'll generate a script to do the file renaming/mv.
Just create the list of files into a file using redirection.  Then copy that list and paste it to the right of all the existing lines using normal vim capabilities.  Then use vim search and replace to modify the target filename as needed.  Lastly, insert the 'mv ' in front of every line.

So in the end, there's a script file that looks like:
```

mv nnnn-nn-nn_nn.nn_00_STRING.txt  nnnn-nn-nn_nn.nn_new_STRING.txt
mv nnnn-nn-nn_nn.nn_00_STRING.txt   nnnn-nn-nn_nn.nn_new_STRING.txt
....
```
The only worry is that a new target filename collides with an existing file.  If the example you've shown is used, I'd just use rename. 
```
$ rename 's/_00_STRING.txt/_new_STRING.txt/g' *txt
```
The .txt isn't really needed. In fact, if _00_ or 00 is unique in all the files, then
```
$ rename 's/00/new/g' *xt
``` is many fewer characters.

If there is any worry about filename collisions, make backups for everything first.

---

### Post by dragonfly41 on 2019-10-04
pyRenamer (GUI) ?

---

### Post by Skaperen on 2019-10-04
by default, [COLOR=#006400][FONT=courier new]**rename**[/FONT][/COLOR] will not replace existing files:
```

lt2a/forums /home/forums 42> ls -dl foo bar
/bin/ls: cannot access 'foo': No such file or directory
/bin/ls: cannot access 'bar': No such file or directory
lt2a/forums /home/forums 43> echo foo >foo
lt2a/forums /home/forums 44> echo bar >bar
lt2a/forums /home/forums 45> ls -dl foo bar
-rw-r--r-- 1 forums forums 4 Oct  4 18:58 bar
-rw-r--r-- 1 forums forums 4 Oct  4 18:57 foo
lt2a/forums /home/forums 46> rename s/foo/bar/ foo
foo not renamed: bar already exists
lt2a/forums /home/forums 47> cat bar
bar
lt2a/forums /home/forums 48> 
```

---

### Post by robertcull1 on 2019-10-05
Thank you guys. This should work.

---

