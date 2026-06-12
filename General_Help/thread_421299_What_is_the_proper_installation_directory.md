---
title: "What is the proper installation directory?"
date: 2007-04-24
forum: General Help
---

### Post by Smuve on 2007-04-24
I'm sure this is Ubuntu 101, but my search terms have all been too general I can't find the answer to my question in the resulting quagmire.  I've done alright with my own, single user system, but this weekend I'll be setting up a computer with Ubuntu that will be used by several family members.  I would like to know the proper directory to install once and be accessible to all users.

1.  In what directory should I install apps like Songbird and Floola that run straight from an executable?
2.  Where should I put other programs that I install from source?  
3.  What if there was a program that I only wanted to install for a single user?

Thanks in advance.

---

### Post by Compyx on 2007-04-24
If you want programs installed system-wide, you should put them in /usr/local (executables go in /usr/local/bin, libraries in /usr/local/lib, et cetera). This is for packages that don't come from the package manager. Usually when building from source, you can specify where the files should be located by passing --prefix=<some path> to configure, eg:
```

./configure --prefix=/usr/local

```
this will put all files into /usr/local, by default, binaries go in /usr/local/bin, manpages in /usr/local/man, you can finetune this by passing the --bindir= and --mandir= options to configure.

If you want to install a program for just one user, put the files in their home-directory (passing --prefix=/home/<username>) to configure (and adding the correct PATH to the users .bashrc).

If you want to install programs for some users, you're better off creating new groups and assigning users that may use a specific application to that group (and settings the correct group for the files).

---

### Post by Smuve on 2007-04-24
Thanks Compyx, that's exactly what I was looking for.  And thank you for such a nice, detailed explanation.  I've got a couple bad habits to break since my transition to Linux and I* really* want to do things the right way.

---

