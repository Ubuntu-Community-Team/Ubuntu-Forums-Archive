---
title: "symbolic link (ln -s) question - destination confusion"
date: 2016-03-09
forum: General Help
---

### Post by sonicwind on 2016-03-09
Hey guys.

The man page for the ln (link) command uses the term  "destination" but not under the synopsis. I'm confused whether  "destination" is referring to the TARGET or the LINK NAME.

So in an example of:

ln -s mytargetfile mysymlink

which is considered the destination? mytargetfile or mysymlink?

I ask because the -f (force option) says it will "remove existing destination files".

To  me the destination file would be the TARGET but I was reading how you  can rename/change/modify the TARGET without deleting the symlink first  by doing:

ln -f -s mynewtargetfile mysymlink

I must  understand destination wrong because that would mean your data  (mytargetfile) gets deleted upon renaming rather than the link itself?

Obviously I'm confused. Help!

---

### Post by Dennis N on 2016-03-09
Suppose you have symbolic link A with target B ( A --> B)
You want to change the target to C instead.
**ln -sf C A** will do that in one command, creating (A --> C)
File B is still there. It is not deleted.

Try an experiment to see how it works:

```
dmn@Roxanne:~/work/test$ ls
file1.txt  file2.txt  file3.txt

dmn@Roxanne:~/work/test$ ln -s file1.txt mydefault

dmn@Roxanne:~/work/test$ ls -l
total 0
-rw-rw-r-- 1 dmn dmn 0 Mar  9 10:10 file1.txt
-rw-rw-r-- 1 dmn dmn 0 Mar  9 10:10 file2.txt
-rw-rw-r-- 1 dmn dmn 0 Mar  9 10:10 file3.txt
lrwxrwxrwx 1 dmn dmn 9 Mar  9 10:11 mydefault -> file1.txt

dmn@Roxanne:~/work/test$ ln -sf file2.txt mydefault

dmn@Roxanne:~/work/test$ ls -l
total 0
-rw-rw-r-- 1 dmn dmn 0 Mar  9 10:10 file1.txt
-rw-rw-r-- 1 dmn dmn 0 Mar  9 10:10 file2.txt
-rw-rw-r-- 1 dmn dmn 0 Mar  9 10:10 file3.txt
lrwxrwxrwx 1 dmn dmn 9 Mar  9 10:12 mydefault -> file2.txt

```

You see file1.txt did not get erased. I agree the wording there is confusing.

---

### Post by sonicwind on 2016-03-09
Thank you so much, Dennis N!

That man page is confusing.

---

