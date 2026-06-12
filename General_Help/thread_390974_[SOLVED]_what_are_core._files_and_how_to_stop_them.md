---
title: "[SOLVED] what are core.**** files and how to stop them?"
date: 2007-03-22
forum: General Help
---

### Post by dougfractal on 2007-03-22
What are these files and how to I stop them.

-rw------- 1 mar mar 138M Mar 21 14:57 ./students/mar/core.7417
-rw------- 1 tzv tzv 106M Mar 21 13:30 ./students/tzv/core.13288
-rw------- 1 tzv tzv  92M Mar 21 15:03 ./students/tzv/core.17816
-rw------- 1 tzv tzv 115M Mar 22 14:17 ./students/tzv/core.5107
-rw------- 1 tzv tzv 992K Mar 22 14:43 ./students/tzv/core.5156
-rw------- 1 tzv tzv 107M Mar 22 14:31 ./students/tzv/core.5177
-rw------- 1 tzv tzv 107M Mar 22 10:55 ./students/tzv/core.5191
-rw------- 1 tzv tzv 107M Mar 21 10:18 ./students/tzv/core.8002

I run a nfs debian file server with ubuntu clients. 
These files are crippling my disk space.

I can either stop the dumps (HOW) or create cron script to find and destroy. ( could someone tell me the reg. expression for it as I don't wish to delete core.js for example)

Any Help cheers

Doug

---

### Post by Damaniel on 2007-03-22
These are core files, which are created when a program crashes.  If you run 'file <name of the core file>', you should be able to see the name of the program that is crashing and creating them.

Apparently you can modify the file '/etc/security/limits.conf' to turn off the creation of core files, but I haven't tried it myself so I don't know if anything is needed besides adding the appropriate line to the file.

---

### Post by dougfractal on 2007-08-05
I never thanked you Damaniel
cheers ;-)

Doug

---

