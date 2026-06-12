---
title: "lacking regexp knowledge with fmirror"
date: 2008-04-02
forum: General Help
---

### Post by giumbolo on 2008-04-02
Hi everybody, I admit I don't have a deep undertanding of Regexp. I'm looking for a suggestion on how to make fmirror backup all the files and directories inside a directory.

In few words, I'm required to write a line as follows ...
             include:  [i][x][n]{p|f} pattern
              A regex pattern that, if matched in a particular file/path-name,
              should be mirrored.  This  will  override  any  exclude-patterns
              encountered after this. Equivalent to -i command line option.

              The options are identical with the exclude options.

Say that I want to specify the whole content of the directory /www/site_one. 
Assumed that "p" stands for filename including pattern) and "f" stands for the file only,
what shall I write for pattern to indicate every file and directories? 

Thanks in advance
Elio

---

### Post by justleen on 2008-04-02
include: /www/site_one|*

just a hunch, never used fmirror (but this is what i gther from googling)

---

### Post by giumbolo on 2008-04-02
Thanks Justleen. Tried, But id didn't work.

---

### Post by justleen on 2008-04-02
/www/site_one|*|*|*

?

---

