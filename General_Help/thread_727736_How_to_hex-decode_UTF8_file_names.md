---
title: "How to hex-decode UTF8 file names?"
date: 2008-03-18
forum: General Help
---

### Post by ben22 on 2008-03-18
Hi,

when importing initially to svn

```
ben3@ubuntu:~/Desktop/Kairos$ svn import /home/ben3/Desktop/folder1/ file:///home/svn/reposfolder/ -m "first import"
```

I get an error

```
svn: Valid UTF-8 data
(hex: 4b 61 69 72 6f 73 20 70)
followed by invalid UTF-8 sequence
(hex: f5 68 69 76)
```

I got a suggestion to hex-decode:
[I]
you could hex-decode the string (treat the numbers as 8-Bit-ANSI-Characters), that should be a part of your filename.[/I]

The problem is: 
How do I know whic[LIST]
[*]h folder / file names I need to hex-decode?
[*]How do I hex-decode
[/LIST]?

Thx,
Ben

---

