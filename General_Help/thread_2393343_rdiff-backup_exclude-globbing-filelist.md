---
title: "rdiff-backup exclude-globbing-filelist"
date: 2018-06-02
forum: General Help
---

### Post by Quarkrad on 2018-06-02
I haven't managed so far to find any info on where the filelist text document is stored and what sort of file it is. I assume it is a plain text file.  If you have something like **sudo /usr/bin/rdiff-backup --exclude-globbing-filelist /home/username ...........** where is the filelist stored, what is it called (assume filelist.txt) and are there any special characters in the list itself or filename?  Normally (to me as a linux newbie) there is often a file location in a string but in the rdiff-backup examples I have seen so far they just refer to 'filelist'.

---

### Post by TheFu on 2018-06-02
From the rdiff-backup manpage (which is really excellent),```

       --exclude-globbing-filelist filename
              Like --exclude-filelist but each line of the  filelist  will  be
              interpreted  according  to  the  same  rules  as  --include  and
              --exclude.
```
and```

       --exclude-filelist filename
              Excludes the files listed in filename.  If filename is handwritâ
              ten  you probably want --exclude-globbing-filelist instead.  See
              the FILE SELECTION section for more information.
```

There are lots of other, similar, options.  Plus, understanding the include/exclude from the manpage is needed.
The filename is not assumed. You have to spell it out. It is specified either using an absolute path or a relative path from the PWD where the program is run.

---

### Post by Quarkrad on 2018-06-02
Sorry to be a bit thick on this one.   If I have a (exclusion) list called toby.txt in usr/bin would I then enter in terminal **sudo usr/bin/rdiff-backup --exclude-globbing-filelist toby.txt /home/username .........**?

---

### Post by TheFu on 2018-06-02
Sometimes we all miss details. We've all been there.   Appears the difference between relative and absolute paths is missing.
usr/bin/rdiff-backup and 
/usr/bin/rdiff-backup
are NOT the same.  The leading / makes all the difference.  

Similarly, 'toby.txt' would only work if it was in the current directory and data inside is correctly formatted.  "globbing" is a simple regex method, if that isn't clear.  Regex is very powerful as a pattern matching language.  I don't use these options, so not positive how they work.  There are rdiff-backup command examples in the forums here.

---

