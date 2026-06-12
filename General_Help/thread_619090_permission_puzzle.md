---
title: "permission puzzle"
date: 2007-11-21
forum: General Help
---

### Post by gian on 2007-11-21
Hello All,

I have setup groups with rwx permissions, but members cannot delete or write files, though they can open them. 

???!

Here is an example:

user alex is member of group sales:
file EXAMPLE has owner john:sales and permissions -rwxrwx---
The folder where the file is saved has drwxrwx--- and is owned by john:sales.
Alex cannot delete EXAMPLE, nor write in the same folder.

What am I missing?

thanks for your time,
ciao,
-Gian

---

### Post by gian on 2007-11-21
just wanted to add that the folder is a SAMBA share set with:
create mask = 0770
directory mask = 0770
valid users = @sales

-G

---

### Post by gian on 2007-11-21
-=update=-

if user alex logs on the unix box, and writes a file in the same folder where permissions are drwxrwx---, the file will have -rw-r--r--.

Why other=r ??!

-G

---

### Post by gian on 2007-11-21
-solved?!-

seems that, to be able to effectively delete the files, you have to set 

writable=yes 

in the relevant [section] of smb.conf

you never stop learning...

-Gian

---

