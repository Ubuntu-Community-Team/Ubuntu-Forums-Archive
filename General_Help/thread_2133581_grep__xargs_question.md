---
title: "grep / xargs question"
date: 2013-04-08
forum: General Help
---

### Post by sinsterizme on 2013-04-08
Hello, just trying to understand a subtlety of these commands.

```

ls | xargs grep "def"

```
returns the same thing as 
```

ls | xargs -i grep -H "def" {}

```

I'm confused since wouldn't the first command fail as the input is a one-line string? And the first defaults by outputting the filenames whereas usually you need to specifiy -H. 

Thank you :)

---

### Post by schragge on 2013-04-08
Strictly speaking, the first command is neither *string* nor necessarily one-line. xargs puts file names as arguments to *grep*. If there are more arguments than system limits allow, they would be split in several lines. And *grep* is able to handle multiple file arguments ```
grep "def" file1 file2 file3 &#8230;
```
By default, grep prints file names if there more than one file argument even if you don't specify **-H**.

BTW, a better way to do the same is ```
grep 'def' *
```

---

### Post by steeldriver on 2013-04-08
also you should be aware that 'ls' isn't safe for this kind of thing, it will break if there are any filenames with spaces:

```

$ echo "thing1" > file1
$ echo "thing2" > file2
$ echo "thing 3" > "file 3"
$
$ ls | xargs grep thing
file1:thing1
file2:thing2
grep: file: No such file or directory
grep: 3: No such file or directory

```

whereas the simple shell glob will work:

```

$ grep thing file*
file1:thing1
file2:thing2
file 3:thing 3

```

---

### Post by sinsterizme on 2013-04-08
Thanks guys. I am aware of the xargs whitespace problem and how to fix it, I was just figuring out how xargs works and now I understand it a little better :) 
Cheers

---

### Post by Vaphell on 2013-04-08
personally i stay away from xargs. I consider it hackish and not helping much when it comes to learning how shell works.
in 99% of cases you can do just fine with pure shell features, like for- or while- loop, which while more verbose, offer better readability. Oneliners are overrated ;-)

---

