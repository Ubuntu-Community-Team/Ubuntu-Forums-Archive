---
title: "GREP help"
date: 2008-01-14
forum: General Help
---

### Post by dbrooke on 2008-01-14
Hello, 

I made the following grep line:

grep -Hinr [pattern] *

This is finding what I want to find.. however, I want to pipe it to a new file.  I tried:

grep -Hinr [pattern] * | vi newfile.txt

but that threw an error.

Any suggestions?

thx,
Donovan

---

### Post by jeffus_il on 2008-01-14
> **dbrooke said:**
> Hello, 

I made the following grep line:

grep -Hinr [pattern] *

This is finding what I want to find.. however, I want to pipe it to a new file.  I tried:

grep -Hinr [pattern] * | vi newfile.txt

but that threw an error.

Any suggestions?

thx,
Donovan

grep -Hinr [pattern] * > newfile.txt

and if you like pipes:
grep -Hinr [pattern] * | tee newfile.txt

---

### Post by peabody on 2008-01-14
Or from within vi

:r! grep -Hinr [pattern]* file

---

### Post by dbrooke on 2008-01-14
nice!  

thanks for the help.

Donovan

---

