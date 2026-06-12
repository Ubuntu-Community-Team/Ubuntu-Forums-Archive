---
title: "How to make a text file with directory content?"
date: 2005-10-31
forum: General Help
---

### Post by jmrush on 2005-10-31
I need a list of the files inside one folder written in a text file.How can I do that?

---

### Post by suRoot on 2005-10-31
Open a terminal...

```
ls /path/to/directory | cat > filelist.txt
```

To append a list of files from another directory to that file, 

```
ls /path/to/directory | cat >> filelist.txt
```

If you want file attributes, add the -l switch to ls.  If you want to include hidden files, add the -a switch.  If you want both, add -la.

---

### Post by 23meg on 2005-10-31
You shouldn't need the "cat" command in between; ```
ls > file.txt
``` should work. See [here]("http://www.linuxcommand.org/lts0060.php") for more on bash I/O redirection.

---

### Post by markthecarp on 2005-10-31
> See [here]("http://www.linuxcommand.org/lts0060.php") for more on bash I/O redirection.

Excellent link 23Meg! I've bookmarked that one for sure.

-mark

---

### Post by 23meg on 2005-10-31
[QUOTE=markthecarp]Excellent link 23Meg! I've bookmarked that one for sure.

-mark[/QUOTE]

Definitely; bash is so beautiful. Here are a few more links you'll enjoy:

[http://www.shelldorado.com/](http://www.shelldorado.com/)
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/)
[http://www.itfreaks.com/tutorials/linux_bsd_unix/](http://www.itfreaks.com/tutorials/linux_bsd_unix/)

---

