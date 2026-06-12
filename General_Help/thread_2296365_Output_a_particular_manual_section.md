---
title: "Output a particular manual section"
date: 2015-09-25
forum: General Help
---

### Post by CkDGTAT on 2015-09-25
Hi,

I need to access only the FILES section of a manual. How can I output it to tty?

Thank you

---

### Post by Habitual on 2015-09-25
```
man <manpage> | less +/^FILES
```

---

### Post by tgalati4 on 2015-09-25
*info* has an output capability:

> tgalati4@Mint17 /tmp $ info -o which-documentation.txt which
tgalati4@Mint17 /tmp $ cat which-documentation.txt 
*manpages*
File: *manpages*,  Node: which,  Up: (dir)

WHICH(1)                    General Commands Manual                   WHICH(1)



NAME
       which - locate a command

SYNOPSIS
       which [-a] filename ...

DESCRIPTION
       which returns the pathnames of the files (or links) which would be exe&#8208;
       cuted in the current environment, had its arguments been given as  com&#8208;
       mands  in a strictly POSIX-conformant shell.  It does this by searching
       the PATH for executable files matching the names of the  arguments.  It
       does not follow symbolic links.

OPTIONS
       -a     print all matching pathnames of each argument

EXIT STATUS
       0      if all specified commands are found and executable

       1      if  one  or  more  specified commands is nonexistent or not exe&#8208;
              cutable

       2      if an invalid option is specified



Debian                            1 May 2009                          WHICH(1)


Well, I misread the OP's question.  Habitual's method works quite well.

---

