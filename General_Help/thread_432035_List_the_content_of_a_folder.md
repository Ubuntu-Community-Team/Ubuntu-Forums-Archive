---
title: "List the content of a folder"
date: 2007-05-03
forum: General Help
---

### Post by ubuntu_jazzbach on 2007-05-03
HI !!!!

Does anyone know how to list the content of a folder recursively in a tree form using the console ???

I'd like an output like this:

[HTML]
Folder
   |---subfolder1
   |---subfolder2
   |---subfolder3
            |--- file A
            |--- subsubfolder1
                       |--- file B
   |---subfolder 4
[/HTML]

---

### Post by taurus on 2007-05-03
You mean something like

```
ls -la -R directory
```

---

### Post by ubuntu_jazzbach on 2007-05-03
I was looking for a command that could do something like"pstree -p" but with the folders, instead of the processes

---

### Post by WW on 2007-05-03
First,
```

$ sudo apt-get install tree

```
This will install the command **tree**.

For example,
```

~/tmp2$ ls -p
dir1/  dir2/  file1  file2
~/tmp2$ tree
.
|-- dir1
|   |-- fileA
|   `-- fileB
|-- dir2
|   `-- dir3
|       |-- fileX
|       |-- fileY
|       `-- fileZ
|-- file1
`-- file2

3 directories, 7 files
~/tmp2$

```

---

### Post by ubuntu_jazzbach on 2007-05-03
Excelente !!!!! Thank You Very Much !!!!!

---

