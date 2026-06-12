---
title: "Big Problem with graphiz-cairo"
date: 2007-01-20
forum: General Help
---

### Post by craz on 2007-01-20
Every time I try to install a package I get the error message: 
```
E: graphviz-cairo: subprocess post-installation script returned error exit status 127
```
In the terminal it tries to install or uninstall this "package" every time, but it cannot find it, because its not there. Here is the terminal output when I try to install a program:
```
Setting up graphviz-cairo (2.8-2) ...
/var/lib/dpkg/info/graphviz-cairo.postinst: 11: dot: not found
dpkg: error processing graphviz-cairo (--configure):
 subprocess post-installation script returned error exit status 127
```
Here is the terminal output when I try to uninstall graphviz-cairo:
```
Removing graphviz-cairo ...
/var/lib/dpkg/info/graphviz-cairo.postrm: 11: dot: not found
dpkg: error processing graphviz-cairo (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 graphviz-cairo
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
What is going on?  I have not been able to find a solution anywhere.  Thanks for your time.

---

### Post by craz on 2007-01-21
Anybody ever had this problem?

---

### Post by craz on 2007-01-23
This is really a pain.  There is no reference in the repositories and I have no idea where this is coming from.  If anybody knows anything about this, please share.

---

### Post by craz on 2007-01-23
*bump*

Sorry but there arent any answers anywhere and this is very frustrating.

---

### Post by craz on 2007-01-24
I am assuming nobody had this problem then.  Oh well...
I dont know what I will do...

---

### Post by rosendahl on 2007-01-25
I have the same problem:(

---

### Post by craz on 2007-01-25
For anyone who needs to know I found a solution.  It is to run
```
sudo rm /var/lib/dpkg/info/graphviz-cairo.post*
sudo aptitude remove -f graphviz-cairo
```
in the terminal.  That should fix it.

---

### Post by zupermanz on 2007-02-05
I had the same problem and fixed it this way! thanks

---

