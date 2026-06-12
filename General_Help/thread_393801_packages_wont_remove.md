---
title: "packages wont remove"
date: 2007-03-26
forum: General Help
---

### Post by matt91 on 2007-03-26
i am trying to remove the package postfix to reinstall it and get an error. it is now giving this error for any other packages i try to remove. here is from the terminal:
> 
root@server:~# apt-get remove postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  postfix
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  postfix
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2494kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 45200 files and directories currently installed.)
Removing postfix ...
/var/lib/dpkg/info/postfix.prerm: 41: /etc/init.d/postfix: not found
dpkg: error processing postfix (--remove):
 subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server:~#


can anybody help. iv tried various other commands to force which doesnt make any difference.

Matt

---

### Post by eljalill on 2007-03-26
Someone here had the same error code:
[http://ubuntuforums.org/showthread.php?t=306480](http://ubuntuforums.org/showthread.php?t=306480)

Maybe this works for you as well?

---

### Post by matt91 on 2007-03-26
iv tried them instructions and they do not help, it is doing this with all installations i have just noticed aswell as removals.

---

### Post by zvacet on 2007-03-26
```
sudo aptitude remove package
```

---

### Post by matt91 on 2007-03-26
im getting the same error with that

---

### Post by matt91 on 2007-03-26
anybody know what to do. i have a server which will not install, remove or update packages. i cannot reinstall as the server is heavily configured.

---

### Post by matt91 on 2007-03-26
(bump)

---

### Post by matt91 on 2007-03-26
please help:confused: :confused:

---

### Post by matt91 on 2007-03-26
please, does anybody have a solution. i need this solving.

Thank you.

---

### Post by foxiness on 2007-03-27
see what i found [http://ubuntuforums.org/showthread.php?t=394282](http://ubuntuforums.org/showthread.php?t=394282) ,because i has the same problem

---

