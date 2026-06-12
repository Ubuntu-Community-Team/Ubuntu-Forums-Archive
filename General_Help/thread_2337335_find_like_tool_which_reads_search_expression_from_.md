---
title: "find like tool which reads search expression from file?"
date: 2016-09-16
forum: General Help
---

### Post by cppljevans on 2016-09-16
I like find, except when the search expression gets complicated.
I find it a hassle to continually escape parenthesis.  For example,
in one Make file, I had:

include $(FIND.mks)/FILE.excludes.mk
FIND.source?=$(HOME)/prog_dev/backup/test.dir
FILT:= \
     \(  -false\
      -o -path $(FIND.source)/none1 -prune\
      -o -path $(FIND.source)/none2 -prune\
     \) -fprint /dev/null\
  -o $(FILE.excludes)\
     \(  -false\
      -o -path $(FIND.source)/partial/partial1/whole/\*\
      -o \! -path $(FIND.source)/partial/\*\
     \) -print\
#

It would be so much easier if the find command had an option something like:

  --expr=FILE

which would cause the search expression to be read from a file.
Similar options are available for the tar command and duplicity.

Is there any variation of find out there that has this convenient feature?

-regards,
Larry

---

