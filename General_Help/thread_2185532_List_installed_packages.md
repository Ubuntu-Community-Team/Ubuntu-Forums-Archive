---
title: "List installed packages"
date: 2013-11-03
forum: General Help
---

### Post by marinecomm on 2013-11-03
I came across this code to make a list of all installed packages and the write it to a text file if you want it to. The problem is that sometimes the code works and sometimes it doesn't. I can't figure out why it doesn't work sometimes. The code is:

**./user_installed_packages**

When it doesn't work I get the following error message: **bash: ./user_installed_packages: No such file or directory**

Any thoughts or ideas as to what could be causing it? I'm running Xubuntu 12.04 64-bit.

---

### Post by mörgæs on 2013-11-03
If you follow the link in my signature there's a description.

---

### Post by steeldriver on 2013-11-03
The command **./user_installed_packages** says "run the program (or script) called user_installed_packages that's in the current directory" - so if the file is **not** in the current directory, you'll get that error. You can see what the current directory is by typing

```
pwd
```

and you can list the contents (to check the user_installed_packages file is there) using

```
ls
```

If you want to be able to run the program/script regardless of what directory you're in, you should put it in a directory that's on your executable path e.g. /home/username/bin (for personal programs) or /usr/local/bin (for everyone). You can check the current executable search path using

```
echo $PATH
```

---

### Post by marinecomm on 2013-11-03
Morgaes: thank you. that did the trick.

---

