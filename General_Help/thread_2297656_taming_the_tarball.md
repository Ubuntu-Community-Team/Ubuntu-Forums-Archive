---
title: "taming the tarball"
date: 2015-10-05
forum: General Help
---

### Post by maclenin on 2015-10-05
I am trying to remotely tar files within a target directory without taking the target directory with me - if that makes any sense....

tar directory:
```
remote/
test.tar
```
target directory:
```
directory/
file0
file1
file2
```
tar command:
```
$ tar -cvf /remote/test.tar -C /directory/ .
```
tarball current contents:
```
./ <----- current folder - which I do NOT want - and which I have to click through to get to the files
file0
file1
file2
```
tarball desired contents:
```
file0
file1
file2
```

Thanks for any guidance!

---

### Post by HermanAB on 2015-10-05
Use the -C option to change the remote directory before making the tar ball.  The resulting directory structure in the tar ball will be  relative to that new point.  So to do what you want, change directory into the target directory, then you can still tell tarr to put the tar ball itself somewhere else if you want, to prevent  recursive tar error.  It is smart enough not to try to include the tar in the tar - it will just complain a bit.

---

### Post by maclenin on 2015-10-06
...and that's Read The _ Manual for details, *please*....

So - are you suggesting:
```
tar -C /directory/ . -cvf /remote/test.tar
```
I ran it - with the same result...it still grabs the current directory (".") along with its contents....
```
./
test0
test1
test2

```
...still in search of, *simply*....
```
test0
test1
test2
```
...if I remove the "." tar becomes cowardly....

---

### Post by Nixarter on 2015-10-06
you might find something useful on this thread.  I didn't see a simple --no-parent option, but there seem to be other ways...

[https://stackoverflow.com/questions/5695881/how-do-i-tar-a-directory-without-retaining-the-directory-structure](https://stackoverflow.com/questions/5695881/how-do-i-tar-a-directory-without-retaining-the-directory-structure)

and if I misunderstood what you were asking, just ignore me. :o

---

### Post by maclenin on 2015-10-06
**Nixarter!**

Thanks for the link. The *--directory* and *cd* options recommended get me to a similar place - and none (yet) free me of:

```
./
```

Onward!

---

### Post by Nixarter on 2015-10-06
wow, that's odd.

Have you considered making a new folder in that folder, and then putting everything in that subfolder?  Then you would still get the ./ but it would be empty at least.

---

### Post by jim_deadlock on 2015-10-06
```
$ tar -cvf /remote/test.tar -C /directory/ *
```

. means directory
* means files

---

### Post by maclenin on 2015-10-10
...I'll reply with a brain teaser:

Create test.tar in /backups/ containing only the contents of /directory/

Set up:
```
$ mkdir ~/Desktop/tar_test
$ cd ~/Desktop/tar_test
$ mkdir backups directory
$ cd directory
$ touch t0 t1 t2
$ cd ..
```
Run tar A...
```
$ tar -cvf ~/Desktop/tar_test/backups/test.tar -C ~/Desktop/tar_test/directory/ *
```
...does your A result differ from:
```
tar: backups: Cannot stat: No such file or directory
tar: directory: Cannot stat: No such file or directory
tar: Exiting with failure status due to previous errors
```
Run tar B...
```
$ tar -cvf ~/Desktop/tar_test/backups/test.tar -C ~/Desktop/tar_test/directory/ .
```
...does your B result differ from:
```
./
./t0
./t1
./t2
```
Still searching for a tar containing only (when run according to the rules of the teaser):
```
t0
t1
t2
```
NB: Run this tar C to see the tar result I am after (though derived differently):
```
$ cd ~/Desktop/tar_test/directory/
$ tar -cvf test.tar *
```
Thanks for any ideas!

---

### Post by maclenin on 2015-12-13
Just following-up....

In this example:

/ <--- tar directory (local)

/ <--- parent directory (remote)
a <--- directory or file
b <--- directory or file
c <--- directory or file

Is there a way to tar only the contents of a parent directory - remotely (i.e. tar file will be created in a separate local directory) - using a wildcard (. or * or other) - and avoid 'tarring' the parent directory (as well)?

YES (what I AM looking to archive):
```
a
b
c
```

NO (what I am NOT looking to archive):
```
./
./a
./b
./c
```

Thanks for any help!

P.S. This ( tar -cvf test.tar * ) works LOCALLY (from within the parent directory) but NOT REMOTELY (from the tar directory using the -C option).
P.P.S. The -C option does NOT work with the wildcards '.' or '*'

---

### Post by matt_symes on 2015-12-13
Hi

> $ tar -cvf /remote/test.tar -C /directory/ *

The problem you have with the above example is the shell is performing expansion on the wildcard before being passed into the tar command.

> $ tar -cvf /remote/test.tar -C /directory/ .

This will implicitly add the containing folder's path as it's what you're asking tar to do.

You can do this with a sub shell though

```
(f_=$(pwd);cd test; tar -cvf test.tar *; mv test.tar "$f_"; )
```

Get the current directory. Move into the directory directory to tar. run the tar command. move the tar file to the old directory. Exit the subshell.
```

matthew-xu-16-04:/home/matthew:0 % ls test.tar
ls: cannot access test.tar: No such file or directory
matthew-xu-16-04:/home/matthew:0 % ls test 
a  b  c  d  t
matthew-xu-16-04:/home/matthew:0 % (f_=$(pwd);cd test; tar -cvf test.tar *; mv test.tar "$f_"; )
a
b
c
d
t
matthew-xu-16-04:/home/matthew:0 % ls test.tar                                                  
test.tar
matthew-xu-16-04:/home/matthew:0 % tar -tf test.tar 
a
b
c
d
t
matthew-xu-16-04:/home/matthew:0 %
```

You can then generalise the subshell and add as a function into your shell. 

Something like this should work

```
function tar_remote { (f_=$(pwd);cd "$2"; tar -cvf "$1" *; mv "$1" "$f_"; ) }
```

and you would call it like so

```
tar_remote test.tar /path/to/directory
```

The above is untested so it may need tweaking and/or fixing but you get the general idea.

Kind regards

---

### Post by maclenin on 2015-12-19
**matt_symes!**

Fabulous - I've been buried in and by other things but will test and reply - with tweaks and fixes (should I find myself worthy of producing such)!

Thank you!

---

