---
title: "Ok...total brain fart here...."
date: 2008-02-11
forum: General Help
---

### Post by rayj00 on 2008-02-11
This is probably one of the most easiest of questions and I know I should know the answer...

How do I change it so when a user or even admin creates a file, the permissions on the new file are 700?
I know how to change it once created, but I want the default to be 700.

Thanks,

Ray

---

### Post by chadeldridge on 2008-02-11
[http://ubuntuforums.org/archive/index.php/t-220974.html](http://ubuntuforums.org/archive/index.php/t-220974.html)

---

### Post by rayj00 on 2008-02-11
Doesn't seem to work for me.

I've tried umask=022 in the .bashrc
did:  source ~/.bashrc
I did >tempfile
I did ls -l tempfile
results are: 644 or -rw-r--r--


I've tried umask=044 in the .bashrc
did:  source ~/.bashrc
I did >tempfile1
I did ls -l tempfile1
results are: 644 or -rw-r--r--

Ideas?

---

### Post by pointone on 2008-02-11
Uh... actually, that is working.

You want umask=077 for the default permissions to be 700. (Although files will still be created 600; you cannot create a file with the execute bit on.)

Also, I'd recommend setting it in /etc/profile if you want the changes to be system-wide.

See:

[http://www.sun.com/bigadmin/content/submitted/umask_permissions.html](http://www.sun.com/bigadmin/content/submitted/umask_permissions.html)

---

