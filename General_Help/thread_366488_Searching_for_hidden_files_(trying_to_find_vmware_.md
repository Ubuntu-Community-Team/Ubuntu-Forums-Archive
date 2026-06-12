---
title: "Searching for hidden files (trying to find vmware install script)"
date: 2007-02-20
forum: General Help
---

### Post by rainwalker on 2007-02-20
Is it possible to search for hidden files in the File Browser? 
If not, does anyone know where the install script for VMware is? I updated the kernel a while back and it broke vmware so I need to run the script again but I can't find it.
Any suggestions?

---

### Post by aysiu on 2007-02-20
Have you tried Alt-F2 ```
gnome-search-tool
```? That has some extra options for searching for hidden files.

---

### Post by highneko on 2007-02-20
[COLOR="Gray"]# You could use the terminal command find maybe?[/COLOR]
find /directory -iname '*filename*'
[COLOR="Gray"]# Maybe even use it with grep?[/COLOR]
find /directory -iname '*filename.sh*' -exec grep 'string' {} \;

---

### Post by rainwalker on 2007-02-20
EDIT: Nevermind, I found it!

---

### Post by highneko on 2007-02-20
How did you find it? Did you use the great and wonderful bash maybe?

---

### Post by bettlebrox on 2007-02-21
> **rainwalker said:**
> EDIT: Nevermind, I found it!
Can  you told where? It could helpful to someone who comes upon this thread looking for the same thing and save us all from suspense! ;)

I don't have Vmware installed on my Ubuntu laptop, but on my Debian workstation it's 

[INDENT]/etc/vmware/installer.sh[/INDENT]

---

### Post by veloce on 2007-02-21
> **rainwalker said:**
> Is it possible to search for hidden files in the File Browser? 
If not, does anyone know where the install script for VMware is? I updated the kernel a while back and it broke vmware so I need to run the script again but I can't find it.
Any suggestions?

If you have vmware server, then you want vmware-config.pl not the install script.

/usr/bin/vmware-config.pl

---

