---
title: "iconv multiple files"
date: 2007-04-29
forum: General Help
---

### Post by ryu kun on 2007-04-29
Could you please tell me, how can I convert all files in a directory with "iconv"?

I tried to use * as the input file parameter but it didn't work.

---

### Post by yabbadabbadont on 2007-04-30
The iconv manpage indicates that you **must** create a new file when converting.  Then you replace the old file with the new one.  Which is why your attempt failed.  An easier method would be to install the "recode" program.  It is available in the repositories.  When run, it converts the input file in place.  With it you should be able to convert an entire directory of text files at once using "*" as the input file parameter.  However, I've never had the need to run either one, so you will want to do a small test first to be sure that it works properly.

---

### Post by tonic20 on 2008-01-14
try following shell script:
#/bin/bash
LIST=`ls *.php`
for i in $LIST;
do iconv -f cp1251 -t utf8 $i -o $i."utf8";
mv $i."utf8" $i;
done

---

### Post by yabbadabbadont on 2008-01-15
Holy Thread Necromancy Batman!

:lol:

Personally, I would use some form of the "find" command, perhaps combined with a modified version of your script.  Or just call the recode program using the "-exec" option of find.

---

