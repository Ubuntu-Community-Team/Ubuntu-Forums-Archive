---
title: "accessing root owned folders w/ sudo"
date: 2005-06-09
forum: General Help
---

### Post by rjstevens3 on 2005-06-09
Hello, i've been having trouble with sudo. whenever i try to access a folder owned by root, i cannot get in with sudo because

sudo cd [/dir]

reports cd as an unknown function. in other distos, i can su and then access the folders, but i would like to get this working with sudo. Any suggestions?

---

### Post by desdinova on 2005-06-09
[QUOTE=rjstevens3]Hello, i've been having trouble with sudo. whenever i try to access a folder owned by root, i cannot get in with sudo because

sudo cd [/dir]

reports cd as an unknown function. in other distos, i can su and then access the folders, but i would like to get this working with sudo. Any suggestions?[/QUOTE]
 sudo is a one off - so it doesn't work because you could find yourself inside a folder you have no permissions to - kind of like trying to teleport into a locked box ;-) You'd be best using su for this, IMHO

---

### Post by angkor on 2005-06-09
Can't you get access just using 

cd / 

without sudo

---

### Post by rjstevens3 on 2005-06-09
i cannot cd into the directory. i get a privileges error when i try

---

