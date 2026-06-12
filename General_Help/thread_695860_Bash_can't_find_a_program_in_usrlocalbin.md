---
title: "Bash can't find a program in /usr/local/bin"
date: 2008-02-13
forum: General Help
---

### Post by NotPhil on 2008-02-13
I've installed xcheckers in /usr/local/bin/xcheckers-2.2.3. When I try to launch it from the terminal, I'm told:
```
xcheckers
bash: xcheckers: command not found
```
When I check the paths for Bash, I see:
```
echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
```
When I launch the same game in the terminal from another folder installed on my Desktop with ./xcheckers it runs.

Does anyone know why?

---

### Post by pointone on 2008-02-13
PATH is not recursive, AFAIK. If your executable is /usr/local/bin/xcheckers-2.2.3/xcheckers, then your path will need to include /usr/local/bin/xcheckers-2.2.3. Easy solution is to simply create a symlink from the executable to /usr/local/bin.

---

### Post by NotPhil on 2008-02-13
> **pointone said:**
> Easy solution is to simply create a symlink from the executable to /usr/local/bin.The link will launch the program, but XCheckers calls some other programs in its directories, and it can't seem to find them if I launch it from the link.

---

### Post by taurus on 2008-02-13
what if you edit ~/.bashrc

```
gedit ~/.bashrc
```
and add these two lines to the end of it.

```
PATH=$PATH:/usr/local/bin/xcheckers-2.2.3
export PATH
```
Save it and then log out and back in again.  Now, see if you can run that program this time.

---

### Post by geraldm on 2008-02-13
Linux has a cache of available executables.  After you have just installed a new executable it will not be available unless the cache is updated OR you use a fullpath to the executable.  To update the cache you could reboot, or try
```

sudo ldconfig

```
if you use the command "./xcheckers" the shell only looks in the current directory for the xcheckers.

Gerald

---

### Post by NotPhil on 2008-02-13
> **geraldm said:**
> To update the cache [of executables] you could reboot, or try sudo ldconfigDoes ldconfig work for all executable files or only shared libraries? I just tried it, and it couldn't find xcheckers.
> **taurus said:**
> add [the path] to the end of [~/.bashrc].Will PATH= accept wildcards, or will I have to add a line for every folder I put in /usr/local/bin?

---

