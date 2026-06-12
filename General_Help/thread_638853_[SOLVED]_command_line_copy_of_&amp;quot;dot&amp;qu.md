---
title: "[SOLVED] command line copy of &amp;quot;dot&amp;quot; files"
date: 2007-12-12
forum: General Help
---

### Post by pwaldo on 2007-12-12
Hi all,

Anyone know how I can include "dot" files in a copy command?  Dot files are files that have a "." in front of them and are not normally shown with "ls", but "ls -A" shows them.  Consider the following directory:
```
# ls -Al src
total 0
-rw-r--r-- 1 root root 0 Dec 12 14:34 .a
-rw-r--r-- 1 root root 0 Dec 12 14:38 a

```

I want to copy both files to a different location using the cp command:
```
# ls -lA dest
total 0
# cp -av src/* dest
`src/a' -> `dest/a'
# ls -lA dest
total 0
-rw-r--r-- 1 root root 0 Dec 12 14:38 a

```

As you can see, "a" got copied, but ".a" did not, because the wildcard does not include dot files.  I know that I could copy the whole directory with "cp src dest", but I don't want the directory itself copied.  Any thoughts would be greatly appreciated!

Paul

---

### Post by r-mo on 2007-12-12
if you're copying a directory you can

```
cp -R src target
```

that will copy everything in src into a new directory target or say if you wanted to copy all files beginning with "a" hidden or not you could use 2 commands 

```

cp src/a* target
cp src/.a* target

```

you can even use regular expressions to pattern match the file names

---

### Post by mali2297 on 2007-12-12
You can try
```

cp -av src/* src/.[0-z]* dest

```

---

### Post by pwaldo on 2007-12-12
> **r-mo said:**
> if you're copying a directory you can

```
cp -R src target
```

that will copy everything in src into a new directory target or say if you wanted to copy all files beginning with "a" hidden or not you could use 2 commands 

```

cp src/a* target
cp src/.a* target

```

you can even use regular expressions to pattern match the file names

Thanks for the reply, r-mo.

The first solution works if you want to keep the enclosing directory, but I want to copy all files into an existing directory.

The second solution makes me nervous.  I know that ```
cp * existing_dir
```  will copy all files except ones that begin with ".".  I worry that if I do ```
cp .* existing_dir
```I'll get more than I bargained for, like "..".  That would not be good!  Also, I have to [LIST=2]
[*]know that there are dot files and [*]execute an additional command to copy them
[/LIST]Ugh!

---

### Post by r-mo on 2007-12-12
cp src/.* target
will say:

cp: omitting directory `test/.'
cp: omitting directory `test/..'

if you added -R however... I'm unsure

and yes you have to know there are dot files, I don't know of any other way though :(  Just use nautilus, hehe

---

### Post by HermanAB on 2007-12-12
Uhmmmm... never use "dot star" wildcards!

The trouble is that "star" includes "dot", so by using "dot star", you also get "dot dot star" which will go back one directory level.

The trick to copying dotted files is to use "-a".

Cheers,

Herman

---

### Post by psusi on 2007-12-12
> **HermanAB said:**
> Uhmmmm... never use "dot star" wildcards!

The trouble is that "star" includes "dot", so by using "dot star", you also get "dot dot star" which will go back one directory level.

The trick to copying dotted files is to use "-a".

Cheers,

Herman

No, the -a flag tells cp to preserve the file owner and permissions when copying.

I suggest using find to tackle this problem:

find . -maxdepth 1 -type f -exec cp {} destination \;

The -maxdepth tells find not to look in subdirectories, the -type f tells it to only consider normal files, not directories or symlinks and such.  If you ONLY want files that start with . then add -name '.*' ( with the single quotes ) before the -exec.  find is smart enough to ignore "." and "..".

---

### Post by dagnabit dang doohickey on 2007-12-13
If you're currently in the source directory, you can use the following command.
This command will recursively copy everything in your current directory (excluding . and ..) to your target directory.
```
cp -rvt /path/to/target/ `ls -A`
```
The above command becomes somewhat awkward if written for use outside the source directory:
```
cp -rvt /path/to/target/ `ls -A /path/to/source/ | sed 's/^/\/path\/to\/source\//'`
```
Here's a somewhat cleaner version of the above command for use outside the source directory:
```
src='/path/to/source/' ; cp -rvt /path/to/target/ `ls -A $src | sed "s#^#$src#"`
```

---

### Post by bingoUV on 2007-12-13
Just exclude . and .. , this will recursively copy all directories and files in the current directory to the targetDirectory
```

find -not -name . -not -name .. -exec cp {} targetDirectory \;

```

---

### Post by psusi on 2007-12-13
> **bingoUV said:**
> Just exclude . and .. , this will recursively copy all directories and files in the current directory to the targetDirectory
```

find -not -name . -not -name .. -exec cp {} targetDirectory \;

```

find always excludes . and .. so there is no need to explicitly exclude them.

---

### Post by lackhead on 2007-12-13
Note that the matching behavior of * is dependent on your shell, not the command.  In particular, bash will match files starting with . if the GLOBIGNORE variable is not set (this also relates to the dotglob option in bash).  I haven't used tcsh in years (bash rules) so I don't remember the details for that, but I'd suggest starting with the man page for whatever shell you are using if you want to make a tweak to your shell.  If this is a one-time use, then you'll have to explicitly include dotfiles in your pattern match.  Others have mentioned ways to do that, but you can also use the ^ in [] matching:

```

[234] tcsh
[101] paris:~/foo:> ls -l src/* src/.[^.]*
-rw-r--r-- 1 clake support 0 Dec 13 09:28 src/.a
-rw-r--r-- 1 clake support 0 Dec 13 09:28 src/a
[102] paris:~/foo:>                 

```

I hope this helps, 


-c

---

### Post by pwaldo on 2007-12-13
> **lackhead said:**
> Note that the matching behavior of * is dependent on your shell, not the command.  In particular, bash will match files starting with . if the GLOBIGNORE variable is not set (this also relates to the dotglob option in bash).  

By Jove, I think he's got it!  I hadn't even considered this a shell issue, but indeed it is:
```
$ ls *
a

$ shopt dotglob
dotglob         off

$ shopt -s dotglob

$ shopt dotglob
dotglob         on

$ ls *
.dot  a

$ shopt -u dotglob

$ ls *
a
```
So now all I have to do is add "shopt -s dotglob" to my .bashrc and I can copy dot files without having to think about it!!!!

Thanks so much!

---

