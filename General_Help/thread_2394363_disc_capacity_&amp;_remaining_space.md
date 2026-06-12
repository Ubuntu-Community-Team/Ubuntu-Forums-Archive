---
title: "disc capacity &amp; remaining space"
date: 2018-06-15
forum: General Help
---

### Post by wfriedwaldgmail.c on 2018-06-15
first, a general update, having installed the new OS (18) I find it great - a big improvement over the previous OS - for one thing, my track pad somehow now works without a problem.  (in the previous edition, I had to use a mouse... could never figure out why.)

now a basic question: what is the quickest way to ascertain disc capacity & remaining space?  the "finder" windows don't automatically do that, the way they do in the Mac OS.  is there a setting so that they do?

(a follow-up question: what is the easiest way to quickly & simply re-name a file?)

Thanks for everything!

w

---

### Post by flaviomonteiro2013 on 2018-06-15
I like to use gnome-disk-utility ("Disks") to check free space and the layout of my partition table. If in need of an analysis about which files/directories are taking the most space, baobab is usually a great option.

If you prefer command-line tools df -h and ncdu do the same as above, respectively.

---

### Post by Bashing-om on 2018-06-15
wfriedwaldgmail.c; Hello -

For disk usage I find the terminal the more informative.
```

df -h
df -i
cd /
sudo du -sx * | sort -n

```

You may find that 'ncdu' is a better tool in this use case:
```

apt show ncdu

```

and to rename files .. is a functiion of the move command:
```

mv <file1> <new_name>

```
see:
```

man mv

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by deadflowr on 2018-06-15
System Monitor.
The File system tab will show total, free, and used for all filesystems in use.
(the one marked "/" is the default main filesystem.)

> a follow-up question: what is the easiest way to quickly & simply re-name a file?
right click on file, select rename, enter new name.

---

### Post by wfriedwaldgmail.c on 2018-06-15
thanks guys!  Will try and get back to you!

---

