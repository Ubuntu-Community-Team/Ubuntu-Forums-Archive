---
title: "Find files using wildcards"
date: 2024-10-28
forum: General Help
---

### Post by raleigh3 on 2024-10-28
How can I modify this so it finds Blank*.* ?

```
#!/bin/bash
# Faster than P_Find
#  Find files using a replaceble parameter
#
# 	Searches ALL mounted drives
#   ex. Find_File.sh Blank.sh
# 
# find /path/to/dir -name "filename"

[ ! $1 ] && {
echo -e "Error!! No filename given. Searches ALL of /dev/sda2 !!"; exit 1; } || echo -e "Searching for $1"
sudo find / -name $1
```

---

### Post by TheFu on 2024-10-29
This script seems like a waste to me. I must be missing something.  

'*.*' is left over from MSDOS.  Do you really more than '*'?  Forcing it to look for files that have a period in the name seems counter productive. Linux doesn't care about extensions to filenames.  They are useful only for humans, provided they are correct.  Don't believe me?  Copy a PDF file and change the extension to .foo from .pdf.  Using any file manager, double-click on that .foo file ... the PDF reader will still open it.

If you want to find files, the fastest way is by using **locate**.

BTW, if you show clear examples of how you expect the script to work, then we can either correct your expectations or provide a better method, like **locate**.
I know of no way to search "ALL of /dev/sda2", since sda2 may not be mounted or contain a file system.   For any search tools to actually work, we need them to have a file system and that file system to be mounted.  There are other types of storage objects that don't use partitions for file system containers. These show up more and more.

```
locate(1)                         General Commands Manual                        locate(1)

NAME
       plocate - find files by name, quickly

SYNOPSIS
       plocate [OPTION]...  PATTERN...

DESCRIPTION
       plocate  finds  all  files  on the system matching the given pattern (or all of the
       patterns if multiple are given). It does this by means of an index made  by  updat&#8208;
       edb(8) or (less commonly) converted from another index by plocate-build(8).
...
```

**locate** runs an index every day, automatically, for non-USB connected storage.  You can force USB connected to storage to be included, if you like.
By default, both **locate** and **find** are case-sensitive on file names.  Both have methods to disable the case-sensitive nature.
**locate** is sub-second. This is because it uses a pre-indexed DB file.
**find** requires scanning the file system, so it can take minutes or hours.  It takes longer because it is looking "right now".

I always start with **locate** when I'm looking for a file(s).  Chances are, that the file I want is over 1 day old on the system, so locate's index will have it already.

The plocate shown in the manpage above ... I have no idea what that is about.  I've never used plocate.  Ah ...
```
$ ll /usr/bin/plocate /usr/bin/locate
lrwxrwxrwx 1 root root        24 Feb 15  2023 /usr/bin/locate -> /etc/alternatives/locate*
-rwxr-sr-x 1 root plocate 313904 Feb 17  2022 /usr/bin/plocate*
```
They are the same. Locate is a symlink to plocate for some reason that makes little sense to me.

If you want **find** to be faster, restrict the type of objects it looks at in as many ways as you can.
[LIST]
[*]If you know it is a file, don't look at any directories.  Directories are just files with a flag.  This doesn't prevent files in sub-sub-sub-directories from being found, but it will prevent any directory name matches from showing up when you want a file.
[*]If you know the owner of the file, don't look for files with any other owners than the one you want.  Depending on the owner, you may have just removed 99% of the files on the system from extra tests.
[*]If you know the file is less than 30 days old, don't look at any files over 30 days old - which will be 95% of them.
[/LIST]
There are other ways to restrict the time that **find** requires, but those 3 are usually sufficient.

Of course, if you want to search INSIDE files at the contents, then you'll need/want something like **recoll**.

---

