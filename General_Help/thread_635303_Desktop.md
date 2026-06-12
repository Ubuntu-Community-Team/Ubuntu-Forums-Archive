---
title: "? Desktop"
date: 2007-12-08
forum: General Help
---

### Post by thehandyman on 2007-12-08
Hey all, I am new to Linux. I am used to Windows Server OS. Is there an equivalent to that as proposed to user permissions and poilcies such as in NT Server? I am Still downloading this so I cannot do anything as of yet but would like to no more about this. Thanks

---

### Post by sg3524 on 2007-12-08
User permissions under Linux differ fairly significantly from Windows.   If you plan to have multi user access to a Linux server you really need to study up on this.  Linux is a simpler model, it has three attributes per file or directory, and will keep those attributes for the file owner, a group, and the world (everyone not in the other two).

The attributes are r (read), w (write), and x (executable).  A file has to be executable to be run as a program, r (read) option alone is not enough (unlike windows).

Users have one main/primary group, but can belong to as many other groups as you would like to include them in.

I would really recommend finding a good Linux system administrators book and reading through permissions and rights.  Its not a tough learn for anyone who has administered systems like you have.  You just need to understand them from the foundational level to best use them.

If you plan to use Ubuntu, try to find an Ubuntu admin book.

Gram

---

### Post by thehandyman on 2007-12-08
Gram, Thank you very much.

---

