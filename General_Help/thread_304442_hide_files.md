---
title: "hide files"
date: 2006-11-21
forum: General Help
---

### Post by Dr Small on 2006-11-21
Hello. I am a familiar windows user, and with windows, you can hide files and folders.

Now, I noticed in the View Menu, that I can show hidden files and folders.
I was wondering what I have to do, in order to hide files and folders,
as I can not find anywhere of how to do it.

Thanks in advanced,
Dr Small

---

### Post by taurus on 2006-11-21
If you don' want other to see files directories in your $HOME account, you can change the permissions...

```
chmod 700 <filename> or <directory name>
```
But if you don't want anybody to look at anything in your $HOME, then do

```
chmod 700 /home/john
(assuming john is your username...
```

---

### Post by Dual Cortex on 2006-11-21
Simply put a "." at the beginning of the file/directory name to hide them... keep in mind that simply going to View>"Show Hidden Files" will *show* the easily hidden file.
Glad I could help.
:)

---

### Post by Dr Small on 2006-11-21
Thanks for the help.
the . in front of the file name worked :)
Thanks again!

Dr Small

---

### Post by taurus on 2006-11-21
> **Dr Small said:**
> Thanks for the help.
the . in front of the file name worked :)
Thanks again!

Dr Small
But "ls -la" will display it again...

---

### Post by CatKiller on 2006-11-22
Also, if you don't want to see the files, but you don't want to change the name of them either, you can make a file in the same directory called **.hidden** and write the names of the files you'd like hidden in it, one per line.

The files will still show up with an **ls** command, but they'll be hidden in Nautillus.

---

