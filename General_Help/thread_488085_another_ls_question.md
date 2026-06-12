---
title: "another ls question"
date: 2007-06-29
forum: General Help
---

### Post by TeeAhr1 on 2007-06-29
I'm starting to think I just don't get the syntax here.  I want to list all flac files in the current directory and subdirectories.  "ls -R *.flac" gives me nothing.  "ls -R /path/to/files *.flac" lists everything.  What am I doing wrong here?

...

Another side question: what I'm really after here is just a listing of directories that contain flac files.  If anyone can help me out with that, that'd be even better.  Thx, as always...

-pete

---

### Post by tronica on 2007-06-29
to list all of the same filetype try this

```
ls -S *flac
```

---

### Post by croto on 2007-06-29
> 
to list all of the same filetype try this

Code:

ls -S *flac


I think the "-S" option is to sort files according to size (at least that's what the man page says). 

To clarify the syntax, when you use the wildcards "*","?", etc. in the shell, they get expanded before the command runs. What I mean by expansion is the following: *flac, as instance, would get replaced by all the files in the *current* directory that end in "flac". For example if you have the files 1.flac, 2.flac  together with other files and directories in the current directory, then "ls -R *.flac" is equivalent to "ls -R 1.flac 2.flac", which means to list recursively 1.flac and 2.flac. Since none of those is a directory, there's nothing to recurse into. I hope it's not too confusing.

To find all directories that contain files ending in flac, I would do the following:
```

find . -iname '*flac' -printf '%h\n' | sort | uniq

```

Note the '*flac' is quoted to *avoid* the expansion I was mentioning previously. The first part of the command finds recursively, starting at . (current directory) all files that match (case insensitively) the pattern '*flac'. For each file, print the path. Note that there can be many flac files in a single directory, that's why I use sort | uniq, which sorts the input and removes duplicate consecutive lines. Check "man find". It's a powerful command.

EDIT: with 
```

find . -iname '*flac' -printf '%h\n' | sort | uniq -c

```

it reports how many files it found in each subdirectory. Sweet.

---

### Post by TeeAhr1 on 2007-06-30
This is great, thank you!

/off to read man:find
-pete

---

