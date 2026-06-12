---
title: "man pages"
date: 2020-06-05
forum: General Help
---

### Post by yegnal on 2020-06-05
From the man pages of the du command:


-X, --exclude-from=FILE
              exclude files that match any pattern in FILE


       --exclude=PATTERN
              exclude files that match PATTERN


In trying to decipher man pages, I question WHY is -X even listed.   It doesn't work at all with -X.  

I thought the reference may be eluding to the correct usage as -X=FILENAME or -X=PATTERN, so I tried every imaginable iteration, but no. 
I tried -X=pattern, -X= pattern, -X =pattern, -X = pattern, -X pattern 

So why is the -X there at all ?  Is confusing or is it just me

---

### Post by TheFu on 2020-06-05
> **yegnal said:**
> From the man pages of the du command:


-X, --exclude-from=FILE
              exclude files that match any pattern in FILE


       --exclude=PATTERN
              exclude files that match PATTERN


In trying to decipher man pages, I question WHY is -X even listed.   It doesn't work at all with -X.  

I thought the reference may be eluding to the correct usage as -X=FILENAME or -X=PATTERN, so I tried every imaginable iteration, but no. 
I tried -X=pattern, -X= pattern, -X =pattern, -X = pattern, -X pattern 

So why is the -X there at all ?  Is confusing or is it just me

You are misreading.  

The **-X** and the **--exclude-from** both read from a file. The -X reads a file, looks for patterns (regex) inside that file, probably 1 line each, to know what to exclude.

Those are 2 different options.    If you want to have a pattern directly as part of the command, use the --exclude= option instead.  

Why have both?  Because different shells will interpret patters in the command line options differently, so being able to skip that completely means a script can work consistently.

Whenever I think I've found a bug in some fairly mature tool, I go stare in the mirror for 5 minutes to figure out that it is highly unlikely.  I'm probably the problem.  Had to do that once this morning.  No bug.  It was my mistake, as usual.  ;)

---

