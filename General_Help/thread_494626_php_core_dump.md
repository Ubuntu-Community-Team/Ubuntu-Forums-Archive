---
title: "php core dump"
date: 2007-07-07
forum: General Help
---

### Post by box2 on 2007-07-07
i'm trying to capture a core dump for a problem i want to report.  i run: 

$ php crash.php
Segmentation fault (core dumped) 

but i can't find the dump.  would it be the file in /var/crash/ called something like _usr_bin_php5.0.crash ?  this is what i think, but it does not load into gdb when i do 

$ gdb php _usr_bin_php5.0.crash
it gives me: "/var/crash/_usr_bin_php5.0.crash" is not a core dump: File format not recognized

i can however do:

$ gdb php
(gdb) run crash.php
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
etc etc...

(gdb) disassemble
and here it will give me just the area of the function that crashes in assembly, but it's not enough for me to see what is happening from start to finish.

i guess what i'm asking is... am i doing something wrong?  is there a better way to debug?

---

### Post by box2 on 2007-07-07
i've also tried compiling php from source to it's own --prefix and trying to make a php.core dump into the --prefix's bin/ but that's not happening either.

i've tried installing the xdebug library for use with komodo, but it's proving rather difficult to even set up. i've also tried using ddd, but i think you probably need xdebug for that too.  gah it hurts my brain...

---

### Post by box2 on 2007-07-18
apparently i just had to recompile php with debugging support.  woohoo.

---

