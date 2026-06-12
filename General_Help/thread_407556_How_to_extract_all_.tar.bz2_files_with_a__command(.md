---
title: "How to extract all .tar.bz2 files with a  command(s)?"
date: 2007-04-12
forum: General Help
---

### Post by tictacman on 2007-04-12
I find myself wondering how extract all tar.bz2 or for the matter tar.gz files which are located in a single directory. 

First of all I thought that something like ```
tar -jxvf $(ls test/ | grep *tar.bz2)
``` would work but cli spat it back at me. After that I noticed that tar didn't like listed files after the command e.g. file1 file2 file3.

After googling I found a command:

```
find test -maxdepth 1 -exec tar xfvj {} \;
```

Trying it resulted in cli spitting this back at me:

find test -maxdepth 1 -exec tar xfvj {} \;
tar: test: Cannot read: Is a directory
tar: At beginning of tape, quitting now
tar: Error is not recoverable: exiting now

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Invalid argument
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors
bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Error exit delayed from previous errors

bzip2: Compressed file ends unexpectedly;
        perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

tar: Child returned status 2
tar: Error exit delayed from previous errors
flower
pettle

So what is the correct command? And what does  ```
{} \;
``` mean?

---

### Post by raja on 2007-04-12
Why not keep it simple and do it in a loop?
```
for tarfile in `ls *.tar.bz2`
do
    tar -xvjf $tarfile
done
```

---

### Post by tictacman on 2007-04-12
thanks very much :)

---

### Post by bashologist on 2007-04-12
> **raja said:**
> Why not keep it simple and do it in a loop?
```
for tarfile in `ls *.tar.bz2`
do
    tar -xvjf $tarfile
done
```

Why the execution of ls? You forgot to quote your variable. Wouldn't this be better?
```
for i in *.tar.bz2; do tar -xvjf "$i"; done
```

---

### Post by raja on 2007-04-12
Thank you. 
Of course being the bashologist, you would come up with something better !
Am I right that not quoting the variable wont give problems unless the filename has spaces?

---

### Post by bashologist on 2007-04-12
> **raja said:**
> Thank you. 
Of course being the bashologist, you would come up with something better !
Am I right that not quoting the variable wont give problems unless the filename has spaces?

Yep, it's a common mistake tho, we all forget to add quotes sometimes. n_n

Also the backquote is deprecated:
[QUOTE=greybot]The backquote (`) is used in the old-style command substitution, e.g. foo=`command`. This syntax is deprecated in favor of foo=$(command). Backslash handling inside $() is less surprising, and $() is easier to nest.[/QUOTE]

---

### Post by girishv on 2007-04-12
```
find test -maxdepth 1 -exec tar xfvj {} \; 
```

this will try to find all the files in the directory test (As maxdepth is 1). But, all the files may not be tar files and hence the error.

Try something like this (if you still want to use find)

find . -maxdepth 1  -name "*.tar.bz2" -exec tar jxvf {} \;

{} \; is to tell the find command that the resultant file(s) from find should be used as 
the argument for the exec command

Girish

---

### Post by WW on 2007-04-12
Or, to extract all .tar.gz and .tgz files in the current directory:
```

$ ls *.tgz *.tar.gz | xargs -n 1 tar xvzf

```
If you have an alias for ls defined (e.g. alias ls='ls --color'), it is probaby safer to do this:
```

$ /bin/ls *.tgz *.tar.gz | xargs -n 1 tar xvzf

```

---

### Post by bashologist on 2007-04-13
> **WW said:**
> Or, to extract all .tar.gz and .tgz files in the current directory:
```

$ ls *.tgz *.tar.gz | xargs -n 1 tar xvzf

```
If you have an alias for ls defined (e.g. alias ls='ls --color'), it is probaby safer to do this:
```

$ /bin/ls *.tgz *.tar.gz | xargs -n 1 tar xvzf

```

I'm not too familiar with xargs , but if you wanted to use multiple patterns in a loop then you could seperate them by spaces:
```
for i in *.tgz *.tar.gz; do tar xvzf "$i"; done

```
It's also possible to test if the file exists:
```
for i in *.tgz *.tar.gz; do if [ -f "$i" ]; then tar xvzf "$i"; fi; done
```

---

