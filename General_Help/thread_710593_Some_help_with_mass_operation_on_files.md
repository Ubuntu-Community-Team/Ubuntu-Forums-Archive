---
title: "Some help with mass operation on files"
date: 2008-02-28
forum: General Help
---

### Post by schristo on 2008-02-28
Hello everyone. I have a large number of pictures in folders, with the following structure:

Year
-----Month
--------Day
--------------Pic1.jpg
--------------Pic2.jpg
--------Day
--------Day

and so on.

Now I would like to take these pictures and create cbr archives of each 'day' directory (basically rar archives that Evince can read directly). This means that I would ideally run a command to recursively run 'rar a -r' on each directory. I tried writing a bash script using some info I found on the internet, but my problem is that although my bash script can, say 'ls' all the files in a for loop, rar will add *all* the directories in one file, which is not what I want. I don't need to do this from the top directory, going into each month and running the command would suffice. 

So, can someone give me a hint on how to individually rar a list of directories?

---

### Post by kidders on 2008-03-01
Hi there,

Try this...

Create a small test version of the directory structure you described:```
$ mkdir -p test/2008/Jan test/2008/Feb test/2008/Mar test/2007/Jan test/2007/Feb test/2007/Mar
$ cd test
```

Write out a sequence of "rar" commands...```
$ for f in */*; do echo rar a `echo $f | sed 's_/_-_'`.rar $f/*; done
rar a 2007-Feb.rar 2007/Feb/*
rar a 2007-Jan.rar 2007/Jan/*
rar a 2007-Mar.rar 2007/Mar/*
rar a 2008-Feb.rar 2008/Feb/*
rar a 2008-Jan.rar 2008/Jan/*
rar a 2008-Mar.rar 2008/Mar/*
```

Your description of what you're looking for is a little confusing, so I'm not 100% sure I got it right ... You mentioned recursion, but my suggestion doesn't go down that road. If the test command seems to do what you want though, you can try it for real by dropping the "echo" from "do echo rar".

---

