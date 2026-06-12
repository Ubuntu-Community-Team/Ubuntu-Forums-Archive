---
title: "want to change my shell"
date: 2008-06-12
forum: General Help
---

### Post by Red-Shield on 2008-06-12
can any one help me change my shell to cash i am currently using bash is there an apt-get out there i can use or something like that...

---

### Post by RAOF on 2008-06-12
Do you mean 'csh' or 'tcsh'?  **aptitude search cash** doesn't know any shell by the name of 'cash'.

Once you've installed your shell, System->Administration->Users & Groups will let you change your login shell.

---

### Post by unutbu on 2008-06-12
Sorry, I don't know if there is a nice GUI way to do this, but this works:

```
gksu gedit /etc/passwd
```
Search for your user name. You'll see at the end of the line "/bin/bash". Just change it to the shell you want... you said cash, but perhaps you meant csh.

If so, you'll have to install it first:

```
sudo apt-get install csh
```

Once it is installed, csh will probably be located at /bin/csh.

---

### Post by bluepowder7 on 2008-06-12
use the "chsh" command.  "man chsh" if you need to find out more.

and why do you need to make 3 threads with the same question????

---

