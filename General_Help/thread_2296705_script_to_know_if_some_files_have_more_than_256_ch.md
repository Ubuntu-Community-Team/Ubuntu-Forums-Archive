---
title: "script to know if some files have more than 256 characters"
date: 2015-09-28
forum: General Help
---

### Post by alain.roger on 2015-09-28
Hi,

i'm wondering if someone has already wrote a script to check content files from directories if all file are no more than 256 characters long name.
If yes, i would like to display the files that need to be shortened.

thx

---

### Post by spjackson on 2015-09-28
You want to print the name of all files whose filename is longer than 256 characters. Have I got this right? The following will do this for your HOME directory and everything below it. For other directories, replace ${HOME} with whatever you want.
```

find ${HOME} | awk -F'/' '{if (length($NF) > 256) { print }}'

```

Edit:
My mistake, I took it to mean the **name** only, rather than the full path. Such names cannot exceed 255 characters on most current systems. The above code checks the length of the name part, not including any path.

---

### Post by Lars Noodén on 2015-09-28
You should also be able to show the files with long names using [find](http://manpages.ubuntu.com/manpages/trusty/en/man1/find.1.html) by itself

```

find . -regextype posix-basic -regex '.\{256,\}' -print

```

---

### Post by alain.roger on 2015-09-28
basically input should be the folder where i should find all filenames being more than 256 characters long (including sub directories)

---

### Post by alain.roger on 2015-09-28
using something like 
> find . -regextype posix-basic -regex '.*/.\{255,\}'

do the trick... except that it does not include the path :(

---

### Post by Lars Noodén on 2015-09-28
I'd not sure I follow, but if you want to check just the file name, while descending into the subdirectories, you'd still need find.
But pipe it into [grep](http://manpages.ubuntu.com/manpages/trusty/en/man1/grep.1.html) so as to select only the long filenames

```

find . | grep -P '[^/]{255,}$'

```

---

