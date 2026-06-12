---
title: "Need a hand with recursively scanning directories"
date: 2007-09-25
forum: General Help
---

### Post by bb002 on 2007-09-25
I'm trying to scan a directory recursively but i want the output to print absolute paths and not the relative ones that "ls" wishes to give me. is there a command line option i don't know of or a bash script to convert between them?


[quote="'ls -1aR' results in"]
/home/dir1:
file1
file2
file3

/home/dir2/:
file4
file5

/home/dir2/dir3:
file6
[/quote]

but i want the results in this form:
> 
/home/dir1/file1
/home/dir1/file2
/home/dir1/file3
/home/dir2/file4
/home/dir2/file5
/home/dir2/dir3/file6


---

### Post by aaargh486 on 2007-09-25
```
noname@noname:/$find
```

Try find.

---

### Post by bb002 on 2007-09-25
works like a charm! never thought of using find >_<

---

