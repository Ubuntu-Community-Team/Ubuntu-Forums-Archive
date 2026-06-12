---
title: "PATH Environment Variable and sudo"
date: 2006-09-04
forum: General Help
---

### Post by glennric on 2006-09-04
I recently installed TeXLive and tried to change the PATH environment variable.  I edited /etc/bash.bashrc and modified the path there.  This worked for my user.  However, it didn't work for sudo.  If I type "env | grep PATH" I get
```
PATH=/usr/local/texlive/2005/bin/i386-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```
However if I type "sudo env | grep PATH" I get 
```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
```
Oddly enough if I type "echo $PATH" or "sudo echo $PATH" I get the same thinge.  Namely
```
/usr/local/texlive/2005/bin/i386-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
```
If I try "sudo texhash" I get "command not found."
Does anyone know how to properly modify the sudo environment?  By the way I have also tried to modify /etc/environment with the exact same results as above.

---

### Post by coffee-beans on 2006-09-04
I have the exact same problem.  I tried editing the /root/.profile and /root/.bashrc files and didn't get anywhere either.

---

### Post by ivantorresjmz on 2008-01-03
Edit /etc/environment instead.

best,
IT

---

