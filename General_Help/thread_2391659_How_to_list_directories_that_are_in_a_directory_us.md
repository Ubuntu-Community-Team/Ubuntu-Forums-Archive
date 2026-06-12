---
title: "How to list directories that are in a directory using the terminal"
date: 2018-05-11
forum: General Help
---

### Post by PopsTheSailor on 2018-05-11
Lets say I have a directory called Top. Then I have a bunch of files and directories in Top. The directory names are Next1, Next2, and Next 3.

If I CD to Top, what is the terminal command so it shows me Next1, Next2, and Next3 (just the directories within the Top directory)?

---

### Post by sudodus on 2018-05-11
Do you want to see the directories (their names) or the content of the directories? Anyway, try these commands and see what happens,

ls:

```
ls *
```
```
ls -d *
```

find:

```
find -maxdepth 1
```
```
find -maxdepth 2
```

---

### Post by cds60601 on 2018-05-11
> **sudodus said:**
> Do you want to see the directories (their names) or the content of the directories? Anyway, try these commands and see what happens,

ls:

```
ls *
```
```
ls -d *
```



And you may also enjoy using:  l -d *

---

### Post by PopsTheSailor on 2018-05-11
I only want to see the directory names and not the files. None of the above worked. they all came back with too many results. In the old DOS days, it used to be dir *. because when I started in DOS directories couldn't allow extensions so you could use dir *. and it would give me just the directory names.

---

### Post by &amp;KyT$0P# on 2018-05-11
```
find -maxdepth 1 -type d
```

---

### Post by PaulW2U on 2018-05-12
> **PopsTheSailor said:**
> I only want to see the directory names and not the files.
You could also use:
```
tree -d
```
with
```
tree -d -L 3
```
where the number changes the display depth of the tree.

Note: tree isn't installed by default. As with any command there's lots to explore in the man page - **man tree**.

---

### Post by kazakore on 2018-05-12
> **sudodus said:**
> 
```
ls -d *
```



Why does the -a argument to show all not show the hidden directories when combined with the -d argument? (Sure the find and tree commands do so it can be got around but it seems a little strange to me.)

---

### Post by sudodus on 2018-05-12
> **kazakore said:**
> Why does the -a argument to show all not show the hidden directories when combined with the -d argument? (Sure the find and tree commands do so it can be got around but it seems a little strange to me.)

That's a good question. I don't know, but I'm sure someone knows, and will tell us soon :-P

---

### Post by sudodus on 2018-05-12
Please consider also the following command lines (more or less complicated, but you can create aliases and store them in ~/.bashrc, to make your favourite outputs easy to use).

These two long ones escape special characters like spaces in filenames and directory names (via find -ls),

The sorting rules differ between locales, and you get a standard order with LANG=C.

Shows also hidden directories,

```

find -maxdepth 1 -type d -ls|tr -s ' ' '\t'|cut -f 12-|sed 's#^./##'|LANG=C sort

```

Does not show hidden directories,

```

find * -maxdepth 0 -type d -ls|tr -s ' ' '\t'|cut -f 12-|sed 's#^./##'|LANG=C sort 

```

These two shorter ones escape special characters like spaces in filenames and directory names (via ls -b), and select directory via the first character in each output line.

```

LANG=C ls -lba|grep ^d
LANG=C ls -lb|grep ^d

```

Maybe you want to strip everything except the [directory] names.

```

LANG=C ls -lba|grep ^d|tr -s ' ' '\t'|cut -f 9-
LANG=C ls -lb|grep ^d|tr -s ' ' '\t'|cut -f 9-

```

---

### Post by Holger_Gehrke on 2018-05-12
A bit simpler:
```
ls -d */
```
or if you want to see hidden directories, too (extended globbing must be active for that (it is by default))```
ls -d ?(.)*/
```

Holger

---

### Post by Holger_Gehrke on 2018-05-12
> **kazakore said:**
> Why does the -a argument to show all not show the hidden directories when combined with the -d argument? (Sure the find and tree commands do so it can be got around but it seems a little strange to me.)

'ls' without argument(s) behaves like 'ls .'. The option '-d' means: show information about the argument but not their content if they are directories. 'ls -d' and 'ls -d .' will both output a line with just a dot on it. The '-a' option is completely useless in this case, it would deactivate the filtering of hidden files, but there are none which would have been filtered ...

 The situation becomes a bit more complex when you pass a '*' as argument. 'ls' does not know about wildcards. It's the shell that expands them into a list of files which it then passes to 'ls'. Just do 'echo *' and 'ls \*' to see what this means. The asterisk is expanded into the names of 'normal' files, it does **not** get expanded to names beginning with a dot unless the shell option 'dotglob' is set ('shop -s dotglob' to set, 'shopt -u dotglob' to unset ). So, once again the option '-a' can't help; the hidden files were filtered before ls could get at them. If you want to show hidden files when passing wildcards as arguments without playing with shell options, you need an extended glob: 'echo ?(.)*'  would do it (and since in this case 'ls' gets the hidden files as explicit arguments, the option '-a' is useless again).

As you can see to just get file names you actually don't need the 'ls' command, it is only needed if you want additional information about the files or want the list formatted or ordered in a specific way. The option '-l' is actually only the peak of the iceberg, there's a lot more to 'ls'. The manual page to ls can tell you how much more.

Holger

---

### Post by PopsTheSailor on 2018-05-12
Thanks everyone for the tips, options, solutions. I went with tree -d. I was looking for something short and quick. Tree -d did the trick. Special thanks to PaulW2U.

---

