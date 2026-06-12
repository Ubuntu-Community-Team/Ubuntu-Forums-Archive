---
title: "Bash syntax question"
date: 2007-09-07
forum: General Help
---

### Post by zapcojake on 2007-09-07
Hello, I am working on a Linux from scratch install and am having trouble getting my .bash_profile right.  This:

code:  

exec env -i HOME=$HOME TERM=$TERM PS1='\u:\w\$ ' /bin/bash


is what it is supposed to be according to the latest LFS book.  
This is the error I get:  bash: exec: env: not found.   

I've tried adding #!/bin/bash at the beginning and some other things I thought might work but no luck.  My host system is Ubuntu 7.04.

---

### Post by geraldm on 2007-09-07
The program /usr/bin/env is contained in the coreutils package, which should have been
installed in an earlier step in Linux From Scratch.  Check that it is present, and if so,
then use the full pathname; if not, then redo the steps skipped.

Gerald

---

### Post by zapcojake on 2007-09-07
I'm just getting started, I haven't installed anything yet, seems likely my path for user lfs isn't right?

---

### Post by banewman on 2007-09-07
I wonder if the problem is that linux is case sensitive? Try using either home or /home and see if that helps. :)

---

### Post by zapcojake on 2007-09-07
Using the full path as geraldm fixed it.

---

