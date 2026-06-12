---
title: "file types in bash"
date: 2008-05-26
forum: General Help
---

### Post by yojimbosteel on 2008-05-26
I can't seem to find this anywhere. How do I display file types in the bash terminal? I've been exploring the ls command and have figured this much out:

1: With ls, text color is used to denote file type, I just don't know what they mean. I've got the simple ones down like directories and symbolic links but there are many more colors. Is there a list somewhere?

2: The ls -F command will append a symbol rather than a color to denote file type but it's the same problem, I don't know what they mean, not only that, it seems to miss something the colors are getting because the same symbol is used for two different colors. i.e. a text file is white with a blank character afterwards and the file /dev/hda is yellow but also follows with the blank character.

Is there someone that can help?

---

### Post by diaa on 2008-05-26
> **yojimbosteel said:**
> I can't seem to find this anywhere. How do I display file types in the bash terminal? I've been exploring the ls command and have figured this much out:

1: With ls, text color is used to denote file type, I just don't know what they mean. I've got the simple ones down like directories and symbolic links but there are many more colors. Is there a list somewhere?

I did some searching and RTMing(*man ls* and *info coreutils 'ls invocation'*) and I found that you can know(and change) all the colors by running the command
```

dircolors -p|pager

```> **yojimbosteel said:**
> 
2: The ls -F command will append a symbol rather than a color to denote file type but it's the same problem, I don't know what they mean, not only that, it seems to miss something the colors are getting because the same symbol is used for two different colors. i.e. a text file is white with a blank character afterwards and the file /dev/hda is yellow but also follows with the blank character.

Is there someone that can help?

Quoting the docs:
> `-F'
`--classify'
`--indicator-style=classify'
     Append a character to each file name indicating the file type.
     Also, for regular files that are executable, append `*'.  The file
     type indicators are `/' for directories, `@' for symbolic links,
     `|' for FIFOs, `=' for sockets, `>' for doors, and nothing for
     regular files.  Do not follow symbolic links listed on the command
     line unless the `--dereference-command-line' (`-H'),
     `--dereference' (`-L'), or
     `--dereference-command-line-symlink-to-dir' options are specified.

---

### Post by yojimbosteel on 2008-05-26
Thank you, that is really helpful :)

---

