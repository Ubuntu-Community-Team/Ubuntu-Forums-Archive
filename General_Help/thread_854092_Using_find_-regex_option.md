---
title: "Using find -regex option"
date: 2008-07-09
forum: General Help
---

### Post by botfish on 2008-07-09
I am trying to use the find command line tool to find file names in my user dir that include characters other than "a-z", "0-9", "_", ".", and "-".

I have written a small bash script but am having trouble with the regex syntax as the command finds zero files. My regex works ok in Ubuntu GUI search tool.

Can anyone see what I am doing wrong? Thanks for any help.

#! /bin/bash
PATTERN="'[^a-z0-9_.-]'"
find /home/user -regex $PATTERN

---

### Post by justleen on 2008-07-09
- to use ^ for "startin with, then dont include it in the [] that is only for a range

- you say you want "other then starting with", so i assume you want everty thing which does not start with a-z", "0-9", "_", ".", and "-".

- eeach part of the string must be connected with a "." (mind this one! to find any file with a _ in it you'll end up with something like '.*._.*.')

- keep in mind find always starts with a "./"

fifth, mind your quoting :) "''" should be "" (put '' quotes around in the find statement) 
PATTERN="^\.\/.[a-zA-Z0-9_.-].*"
^       = at the start
\.\/.   = ./  escaped with \

to get the reverse use "find . ! -regex $PATTERN

---

### Post by ghostdog74 on 2008-07-09
> **justleen said:**
> - 
- keep in mind find always starts with a "./"


not when full path is given

---

### Post by ghostdog74 on 2008-07-09
> **botfish said:**
> I am trying to use the find command line tool to find file names in my user dir that include characters other than "a-z", "0-9", "_", ".", and "-".

I have written a small bash script but am having trouble with the regex syntax as the command finds zero files. My regex works ok in Ubuntu GUI search tool.

Can anyone see what I am doing wrong? Thanks for any help.

#! /bin/bash
PATTERN="'[^a-z0-9_.-]'"
find /home/user -regex $PATTERN

check the find man page and see what it says with -regex option, especially the part where it talks about matching the whole path. this is what you want, i presume.
```

find . -regex ".*[^a-z0-9_.-]+"

```

---

### Post by justleen on 2008-07-09
sorry, im assuming -regextype=posix-awk, which works differently yet again

edit:

im not quite sure if that is what you want the ^ between the []

now you searching for any char, with the first char after that any char being a-z0-9_.-

say i want to find .mozilla, and a use '.*.[^m]+'  it will find ./.mozilla, but also ./.qemu 




:looks lost:

---

