---
title: "Problems With C-Shell"
date: 2006-08-04
forum: General Help
---

### Post by dafrabbit on 2006-08-04
I'm attempting to write a c-shell script using a c-shell taken off the ubuntu repos, version # 20050313-1.

However, it appears that it does not support certain conventions that worked in the other c-shell I've used, in red hat distributions like: "$#". It returns an error message "illegal variable name".

This is the code snippet I am attempting to execute:

# Check the command arguments.
#if ($# < 1) then
#    echo "Usage: $0 filename"
#    echo ""
#    exit 1
#endif

---

### Post by ape on 2006-08-04
Install the tcsh package and your script will work like you want it to (as long as you invoke it using tcsh).

If you really want to continue to use csh, you need to replace $# in your script with ${#argv}.  Then your script will work properly with csh.

Good luck,

--ape--

---

