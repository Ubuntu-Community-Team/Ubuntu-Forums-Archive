---
title: "Changing Permissions on Ubuntu 12.04"
date: 2012-10-28
forum: General Help
---

### Post by KaisaUbun2 on 2012-10-28
So I am trying to install Truecrypt on Ubuntu, and I know I can do it through a terminal, but I like the simplicity of double clicking and then giving it the instruction of running in Terminal. So I go into properties, go to permissions check the box that says allow executing file as program, and soon as I check it... it unchecks itself... any solutionS?

---

### Post by ajgreeny on 2012-10-28
Where, and what is this file that will not allow you to change its permissions?
Are you the owner of the file?
Lets see the output of ```
ls -l /*path/to/truecryptfile*
```which may help show the answer to your query.

---

### Post by KaisaUbun2 on 2012-10-29
I actually solved the problem, I made a silly mistake. Thank you though.

---

