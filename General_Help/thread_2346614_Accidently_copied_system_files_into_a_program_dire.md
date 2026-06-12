---
title: "Accidently copied system files into a program directory"
date: 2016-12-16
forum: General Help
---

### Post by thedarkdragon65 on 2016-12-16
So I was trying to copy an extension file into Inkscape, but somehow accidentally copied system files into it instead. How do I get rid of these files safely? 

When I run the command: **ls**, I get the following directories located in the Inkscape extensions folder:

```
boot  dev extensions  lib32  lost+found  opt   srv  tmp
core  examples.desktop  initrd.img  lib64  mnt    sbin  sys  vmlinuz
```

---

### Post by DuckHook on 2016-12-16
Let's see the ownerships, permissions etc:```
ls -laF
--or simply--
ll
```When posting contents of directories, it's always a good idea to post the long form of the output.

If you did a simple copy, then you probably own the superfluous files and you can just delete them. If you were running as root for some (likely insufficient) reason, then it's not so simple. If ownership is anyone other than yourself, please tell us the background to your inadvertent mistake before doing anything else.

---

### Post by thedarkdragon65 on 2016-12-16
Yea, so running that command, it seems that the directories are owned by root, what should I do in this case?

---

### Post by DuckHook on 2016-12-16
> **thedarkdragon65 said:**
> Yea, so running that command, it seems that the directories are owned by root, what should I do in this case?The question is: "why?"

The only way this could happen is if you were running as root, or copying files with *sudo*. Before "fixing" it, please explain as fully as you can, since the wrong step could bork your system. My worry is that you *moved* instead of *copied*.

---

### Post by thedarkdragon65 on 2016-12-16
I used sudo, because the command **cp -a /source/ . /dest/ **(intending only to copy extensions files from a directory on my Desktop) didn't seem to work at first, so I tried using sudo, but did not expect it to copy system folders.

---

### Post by DuckHook on 2016-12-16
OK. No harm done.

I'll explain the intent first, so that you know what we are trying to do:

When you copy with sudo, the system copies and assigns all copied files root ownership. While this may allow you to copy, it is never a good idea unless you are actually trying to give the resulting file root ownership. But root ownership usually means that you can't work with it as a user. If you are new to the command line, then kudos to you for having the guts to try. But an easier tool to use is midnight commander because its quasi-graphical ncurses layout is much more user-friendly for new users and tends to avoid trouble.```
sudo apt install mc
```You usually invoke it simply with:```
mc
```&#8230;but because your files are owned by root, you will have to give midnight commander root privileges with:```
sudo mc
```In this mode, you are nothing short of god as far as your system is concerned, so ***be careful***. You can now navigate to your errant files (***make sure they are really the errant files and not those under /***) and delete them.

As soon as you are done, exit mc. You don't want to be using it as root for anything other than this one time.

---

