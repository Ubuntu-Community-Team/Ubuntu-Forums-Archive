---
title: "merge two files"
date: 2007-12-21
forum: General Help
---

### Post by Tex-Twil on 2007-12-21
Hello,
I would like to merge two files "line by line".

File one:
```

A
B
C
D
..

```

File two:
```

Alfa
Bravo
Charly
Delta
..

```

I would like to get as a result the following file
```

A Alfa
B Bravo
C Charly
D Delta
..

```

Which means that for all lines I want to echo line i from file 1 and line i from file 2 into line i of the result file

Any ideas ?

thanks,

---

### Post by mali2297 on 2007-12-21
Suppose the files are called *file1.txt* and *file2.txt*. Then just use the command
```

paste file1.txt file2.txt > file3.txt

```
to get the merged content in file3.txt.

The default delimiter is TAB. If you want to use SPACE instead, do
```

paste -d" " file1.txt file2.txt > file3.txt

```

---

### Post by Tex-Twil on 2007-12-21
Great ! 
Linux rocks !!

Thanks

---

