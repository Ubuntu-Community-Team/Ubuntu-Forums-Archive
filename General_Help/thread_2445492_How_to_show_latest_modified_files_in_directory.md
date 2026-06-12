---
title: "How to show latest modified files in directory ?"
date: 2020-06-15
forum: General Help
---

### Post by petrogromovo on 2020-06-15
Hello,
If there is a way in Kubuntu 18 to show latest modified files in directory
(optionally with subdirectories) ?
In console or some utility ?

Thanks!

---

### Post by TheFu on 2020-06-15
find?
ls -rt?

For commands that don't have a built-in sort, we can use '**sort**' and specify to column to be sorted. By default sort starts from the left, but any delimiter can be set and any column number can be used to sort lines.
From the sort manpage:
```
       -h, --human-numeric-sort
              compare human readable numbers (e.g., 2K 1G)

       -n, --numeric-sort
              compare according to string numerical value

       --sort=WORD
              sort according to WORD: general-numeric  -g,  human-numeric  -h,
              month -M, numeric -n, random -R, version -V

       -k, --key=KEYDEF
              sort via a key; KEYDEF gives location and type
```

```
$ sort -k 4   input.file 
```
will sort on the 4th field.  input.file can be stdin, so pipelining is fine.
```
ls -l |sort -k5 -h
```
sorts on file size.

Recursive and reverse order?
```
ls -Rl |sort -k5 -hr|more
```

Lots of other options hidden  in the manpages on every Linux system.

---

### Post by SeijiSensei on 2020-06-15
```
ls -lt
```

gives a full ("-l") file listing sorted by last modification date. Use "-ltr" to put the most recent ones at the bottom of the list.

In Kubuntu, you can sort any directory using Dolphin by clicking on the appropriate header in a "details" listing. It can be selected via the right-most of the three view icons, the one with two empty boxes in the top row and a filled-in box on the right of the second row.

---

