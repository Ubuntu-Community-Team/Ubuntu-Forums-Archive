---
title: "Wildcards and rm -r"
date: 2016-04-26
forum: General Help
---

### Post by jerome1232 on 2016-04-26
I popped into my music directory to remove some duplicates, all had (1) in their filename so I ran ```
rm -rf *(1)*
``` well that didn't do what I thought. It deleted my entire music library! So while that is redownloading from the cloud I'm wondering what did I screwed up about my wildcards?

---

### Post by Bashing-om on 2016-04-26
jerome1232; Hey ....

The way I see it, that command removed every directory and subdirectory and files that contains (1) at any point in the name.

[INDENT][INDENT]ouch;
[INDENT][INDENT][INDENT]system does what system is told
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by steeldriver on 2016-04-26
The expression

```

*(1)

```

is an *extended glob* that matches zero or more occurrences of the digit 1 e.g. given a directory containing the following files

```

$ ls
1  11  11potato  1potato  otherfile  some(1)file somefile

```

then

```

$ echo *(1)
1 11

```

Because it's *zero* or more unfortunately when it's followed by another * the combined expression matches anything (i.e. it's zero or more 1s, followed by anything)

```

$ echo *(1)*
1 11 11potato 1potato otherfile some(1)file somefile

```

To match the literal string (1) with a shell glob (when extglob is enabled) you'd need to escape the parentheses

```

$ echo *\(1\)*
some(1)file

```

---

### Post by jerome1232 on 2016-04-26
@Bashing-om; That was the intention, what I wanted it to do; but that's not what it did. It simply removed every file as if I had ran rm -rf *.


@steeldriver; Thanks! I'll have to give that a try in a test directory.

---

### Post by jerome1232 on 2016-04-26
```
jeremy@main:~$ cd test
jeremy@main:~/test$ ls
jeremy@main:~/test$ touch \(1\)
jeremy@main:~/test$ touch 1
jeremy@main:~/test$ touch file
jeremy@main:~/test$ touch file\(1\)
jeremy@main:~/test$ touch \(1\)file
jeremy@main:~/test$ ls
1  (1)  (1)file  file  file(1)
jeremy@main:~/test$ ls *\(1\)*
(1)  (1)file  file(1)
jeremy@main:~/test$ 

```

Seems to work! Thanks steeldriver!

---

### Post by steeldriver on 2016-04-26
For the record, I would recommend using the `find` command for this kind of thing e.g.

```

find . -name '*(1)*'

```

To delete all regular files recursively starting from the current directory, with confirmation

```

find . -type f -name '*(1)*' -exec rm -i {} \;

```

If you really want to do it without confirmation, 

```

find . -type f -name '*(1)*' -delete

```

If you really wanted to use shell globs (which I don't recommend) then the right way would be to ditch the -r recursive flag on the rm command itself, and instead make the globbing recursive using the shell's globstar option

```

$ shopt -s globstar
$ rm -i **/*\(1\)*
rm: remove regular empty file ‘dir/other(1)file’? n
rm: remove regular empty file ‘some(1)file’? n

```

---

### Post by ajgreeny on 2016-04-26
To avoid potential problems of this sort in future with the rm command it is worth making an alias of **alias rm='rm -i'**  which will warn you before any file is removed by interactively asking y/n?

---

