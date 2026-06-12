---
title: "Problem installing AWN"
date: 2008-02-19
forum: General Help
---

### Post by temp0 on 2008-02-19
I am using Gutsy 64bit, and I have downloaded the AWN and was trying to install it.
I got a few problems with .dev and packages thing when I installed it, but its solved once I downloaded those things.
But, this problem, it seems different (for me:( , becoz I have only been using ubuntu for a week)
and i got this from the teminal.


***INFO*** Generating awn.c from awn.defs
Traceback (most recent call last):
  File "/usr/share/pygtk/2.0/codegen/codegen.py", line 1712, in <module>
    sys.exit(main(sys.argv))
  File "/usr/share/pygtk/2.0/codegen/codegen.py", line 1670, in main
    p.startParsing()
  File "/usr/share/pygtk/2.0/codegen/scmexpr.py", line 113, in startParsing
    for statement in statements:
  File "/usr/share/pygtk/2.0/codegen/scmexpr.py", line 27, in parse
    fp = open(filename, 'r')
IOError: [Errno 2] No such file or directory: '/usr/share/pygtk/2.0/defs/gconf.defs'
make[2]: *** [awn.c] Error 1
make[2]: Leaving directory `/home/gomes/awn-curves/pyawn'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gomes/awn-curves'
make: *** [all] Error 2
gomes@gomes-laptop:~/awn-curves$ 


Could anyone help me out?
Thanks in advance~~

---

