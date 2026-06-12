---
title: "How to check typeof file?"
date: 2017-04-22
forum: General Help
---

### Post by theguy99 on 2017-04-22
How do you determine if an entry in 'ls' command is a directory or file and if it is a file what type of file?

---

### Post by steeldriver on 2017-04-22
If you use `ls` with the **long listing** option, you will see that directories are indicated by a leading `d` in the mode descritpion:

```

$ ls -l
total 4
drwxrwxr-x 2 steeldriver steeldriver 4096 Apr 22 09:21 somedir
-rw-rw-r-- 1 steeldriver steeldriver    0 Apr 22 09:21 somefile

```

Programatically, you can test whether a file object is a directory using the shell's test operators e.g.

```

for f in *; do 
  if [[ -d "$f" ]]; then 
    echo "$f : is a dir"
  fi
done
somedir : is a dir

```

or (more compactly)

```

for f in *; do [[ -d "$f" ]] && echo "$f : is a dir"; done

```

To get a description of a file's content type, you can use the `file` command

```

$ file result.csv
result.csv: ASCII text

```

---

### Post by theguy99 on 2017-04-22
Thanks, yours is the correct answer @steeldriver

---

### Post by ajgreeny on 2017-04-22
It can also be useful to use an alias for **ls** to ensure the output is in colour, and directories are listed first.

I use ```
alias ls='ls -p --color=auto --group-directories-first'
``` in my **~/.bash_aliases** file along with many other aliases, but if you do not have many that you want to use, you can simply add this line to the short list already in **~/.bashrc**.

---

