---
title: "copy random files from each folder to a new folder"
date: 2016-02-24
forum: General Help
---

### Post by sohlinux on 2016-02-24
Hello,

I want to copy 1 file from 500 different folders with maxdepth 1, I have tried the following and I am getting errors

```
find /0/ -maxdepth 1 -mindepth 1 -type f -print0 | sort -Rz | cut -d $'\0' -f-1 | xargs -0 cp -t /0/1

```
cp: missing file operand

anyone know how to do this? thanks

---

### Post by sohlinux on 2016-02-24
or forget random how can I just copy 1 single file from all folders but only 1 deep to another folder, it could be the first file of each folder. thanks

---

### Post by steeldriver on 2016-02-24
I *think *the problem is that 'cut' is adding a newline: here's an alternate approach using bash's 'read' builtin to read a single null-delimited value

```

find *path/to/dir/* -maxdepth 1 -mindepth 1 -type f -print0 | sort -Rz | { IFS= read -r -d '' f; echo mv -- -t *path/to/newdir/* "$f"; }

```

However based on your 'find' command I think it will copy a single file at random from all the regular files at depth one (not one per subdir) - is that what you intended?

---

### Post by sohlinux on 2016-02-24
> **steeldriver said:**
> I *think *the problem is that 'cut' is adding a newline: here's an alternate approach using bash's 'read' builtin to read a single null-delimited value

```

find *path/to/dir/* -maxdepth 1 -mindepth 1 -type f -print0 | sort -Rz | { IFS= read -r -d '' f; echo mv -- -t *path/to/newdir/* "$f"; }

```

However based on your 'find' command I think it will copy a single file at random from all the regular files at depth one (not one per subdir) - is that what you intended?

I just need to copy 1 file from each folder but only 1 folder deep, I managed to copy 1 file with the following

find . -name '*001*.jpg' | cpio -pdm /dest

then to flaten

find . -mindepth 2 -type f -print -exec mv {} . \;

I tried your example but I dont want to move only copy, if I change mv for cp it doesnt work

---

### Post by steeldriver on 2016-02-24
It should work with 'cp' in place of 'mv' - note that I left an echo in for testing purposes though, you will need to remove that once you've confirmed that it's doing the right thing

To copy one file from each I'd just wrap it in a loop e.g. given

```

$ tree
.
&#9500;&#9472;&#9472; 1
&#9474;   &#9500;&#9472;&#9472; file1
&#9474;   &#9500;&#9472;&#9472; file10
&#9474;   &#9500;&#9472;&#9472; file2
&#9474;   &#9500;&#9472;&#9472; file3
&#9474;   &#9500;&#9472;&#9472; file4
&#9474;   &#9500;&#9472;&#9472; file5
&#9474;   &#9500;&#9472;&#9472; file6
&#9474;   &#9500;&#9472;&#9472; file7
&#9474;   &#9500;&#9472;&#9472; file8
&#9474;   &#9492;&#9472;&#9472; file9
&#9500;&#9472;&#9472; 2
&#9474;   &#9500;&#9472;&#9472; file1
&#9474;   &#9500;&#9472;&#9472; file10
&#9474;   &#9500;&#9472;&#9472; file2
&#9474;   &#9500;&#9472;&#9472; file3
&#9474;   &#9500;&#9472;&#9472; file4
&#9474;   &#9500;&#9472;&#9472; file5
&#9474;   &#9500;&#9472;&#9472; file6
&#9474;   &#9500;&#9472;&#9472; file7
&#9474;   &#9500;&#9472;&#9472; file8
&#9474;   &#9492;&#9472;&#9472; file9
&#9492;&#9472;&#9472; 3
    &#9500;&#9472;&#9472; file1
    &#9500;&#9472;&#9472; file10
    &#9500;&#9472;&#9472; file2
    &#9500;&#9472;&#9472; file3
    &#9500;&#9472;&#9472; file4
    &#9500;&#9472;&#9472; file5
    &#9500;&#9472;&#9472; file6
    &#9500;&#9472;&#9472; file7
    &#9500;&#9472;&#9472; file8
    &#9492;&#9472;&#9472; file9

```

then
```

$ for d in {1..3}/; do find "$d" -maxdepth 1 -mindepth 1 -print0 | sort -Rz | { IFS= read -r -d '' f; echo cp -t path/to/newdir/ -- "$f"; }; done
cp -t path/to/newdir/ -- 1/file4
cp -t path/to/newdir/ -- 2/file5
cp -t path/to/newdir/ -- 3/file3

```

---

### Post by sohlinux on 2016-02-24
> **steeldriver said:**
> It should work with 'cp' in place of 'mv' - note that I left an echo in for testing purposes though, you will need to remove that once you've confirmed that it's doing the right thing

To copy one file from each I'd just wrap it in a loop e.g. given

```

$ tree
.
&#9500;&#9472;&#9472; 1
&#9474;   &#9500;&#9472;&#9472; file1
&#9474;   &#9500;&#9472;&#9472; file10
&#9474;   &#9500;&#9472;&#9472; file2
&#9474;   &#9500;&#9472;&#9472; file3
&#9474;   &#9500;&#9472;&#9472; file4
&#9474;   &#9500;&#9472;&#9472; file5
&#9474;   &#9500;&#9472;&#9472; file6
&#9474;   &#9500;&#9472;&#9472; file7
&#9474;   &#9500;&#9472;&#9472; file8
&#9474;   &#9492;&#9472;&#9472; file9
&#9500;&#9472;&#9472; 2
&#9474;   &#9500;&#9472;&#9472; file1
&#9474;   &#9500;&#9472;&#9472; file10
&#9474;   &#9500;&#9472;&#9472; file2
&#9474;   &#9500;&#9472;&#9472; file3
&#9474;   &#9500;&#9472;&#9472; file4
&#9474;   &#9500;&#9472;&#9472; file5
&#9474;   &#9500;&#9472;&#9472; file6
&#9474;   &#9500;&#9472;&#9472; file7
&#9474;   &#9500;&#9472;&#9472; file8
&#9474;   &#9492;&#9472;&#9472; file9
&#9492;&#9472;&#9472; 3
    &#9500;&#9472;&#9472; file1
    &#9500;&#9472;&#9472; file10
    &#9500;&#9472;&#9472; file2
    &#9500;&#9472;&#9472; file3
    &#9500;&#9472;&#9472; file4
    &#9500;&#9472;&#9472; file5
    &#9500;&#9472;&#9472; file6
    &#9500;&#9472;&#9472; file7
    &#9500;&#9472;&#9472; file8
    &#9492;&#9472;&#9472; file9

```

then
```

$ for d in {1..3}/; do find "$d" -maxdepth 1 -mindepth 1 -print0 | sort -Rz | { IFS= read -r -d '' f; echo cp -t path/to/newdir/ -- "$f"; }; done
cp -t path/to/newdir/ -- 1/file4
cp -t path/to/newdir/ -- 2/file5
cp -t path/to/newdir/ -- 3/file3

```


thanks but its just throwing error

what is {1..3} ?

I get error
cp -t /0/ --
find: `2/': No such file or directory
cp -t /0/ --
find: `3/': No such file or directory

I am in the working directory and want to copy to /0

I am placing a dot after find

thanks

---

### Post by steeldriver on 2016-02-24
The
```

{1..3}

```
is a brace expansion that expands to 1 2 3 i.e. a list of the subdirectories in my "test" example. Sorry I really can't help with converting that for your specific subdirectory structure unless you post more details - do you really have a directory /0 (i.e. a directory called 0 at the root level of the filesystem) or did you mean ./0 (a directory called 0 in your current directory)?

---

### Post by sohlinux on 2016-02-24
> **steeldriver said:**
> The
```

{1..3}

```
is a brace expansion that expands to 1 2 3 i.e. a list of the subdirectories in my "test" example. Sorry I really can't help with converting that for your specific subdirectory structure unless you post more details - do you really have a directory /0 (i.e. a directory called 0 at the root level of the filesystem) or did you mean ./0 (a directory called 0 in your current directory)?

yes there is a /0 directory, and the folders have all different names. anyway I have just about managed to do it just by copying the first file from each folder with > find . -name '*001*.jpg' | cpio -pdm /dest I will play around with your example to see if I can figure it out. thanks

---

### Post by steeldriver on 2016-02-24
If you want to run it in EVERY subdirectory of /0 you can simply replace {1..3}/ by /0/*/

```

for d in /0/*/; do find "$d" -maxdepth 1 -mindepth 1 -print0 | sort -Rz | { IFS= read -r -d '' f; echo cp -t path/to/newdir/ -- "$f"; }; done

```

---

### Post by sohlinux on 2016-02-24
> **steeldriver said:**
> If you want to run it in EVERY subdirectory of /0 you can simply replace {1..3}/ by /0/*/

```

for d in /0/*/; do find "$d" -maxdepth 1 -mindepth 1 -print0 | sort -Rz | { IFS= read -r -d '' f; echo cp -t path/to/newdir/ -- "$f"; }; done

```

it says cp: omitting directory `./030216'

030216 is one of the directories inside /0

---

### Post by steeldriver on 2016-02-24
oops sorry should have added -type f

```

for d in /0/*/; do find "$d" -maxdepth 1 -mindepth 1 **-type f** -print0 | sort -Rz | { IFS= read -r -d '' f; echo cp -t path/to/newdir/ -- "$f"; }; done

```

---

### Post by sohlinux on 2016-02-24
> **steeldriver said:**
> oops sorry should have added -type f

```

for d in /0/*/; do find "$d" -maxdepth 1 -mindepth 1 **-type f** -print0 | sort -Rz | { IFS= read -r -d '' f; echo cp -t path/to/newdir/ -- "$f"; }; done

```

perfect!, thanks for your help, I will mark this solved :)

---

