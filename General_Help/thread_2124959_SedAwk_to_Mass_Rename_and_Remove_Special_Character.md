---
title: "Sed/Awk to Mass Rename and Remove Special Characters?"
date: 2013-03-12
forum: General Help
---

### Post by hateborne on 2013-03-12
Hello ladies/gents,

I've got a small problem. I am trying to rename a large number of files on a quote server at work. Many of the file names contain naughties (*, &, ^, `, ~, ?) which cause all kinds of hell[SUP][SUB]1[/SUB][/SUP]. I had a generic few line script written to handle some of this. I cannot seem to figure out how to handle all of it at once. Somehow I've gotten the script to max out the character length allowed for file name length[SUP]2[/SUP]. The initial goal was simply to remove ".COM" from some of the file names (as a program we use interprets dot five letters as the file extension and stops reading the file name there)[SUP]3[/SUP]. After showing this to two gaming buddies, they laughed and said sed can one line this (without a script being needed).

Any suggestions? :confused:


-Hate


1 - It is technically Mac OS X, but the community here is 10x more helpful and 100x less rude! :-D
2 - If a quote was named "1234 * Property Name.fmp12", the script was renaming it "1234 * Property Name 1234 * Property Name 1234 * Property Name 1234 * Property Name.fmp12" (only 2-3x longer)
3 - Trying to rename files containing "WS.COM" to simply "WS" (i.e. '1234 Property Name WS.COM.fmp12' --> '1234 Property Name WS.fmp12")

---

### Post by Vaphell on 2013-03-12
WS.COM -> WS

```
$ f='1234 Property Name WS.COM.fmp12'
$ echo "${f/WS.COM/WS}"
1234 Property Name WS.fmp12
```

```
for f in *WS.COM*; do echo mv -- "$f" "${f/WS.COM/WS}"; done   #remove echo if printout is ok
```

what should happen with uglies? they should be stripped?
```
$ f='some nasty * & looking ^ !filename'
$ echo "${f//[\!\*\&\^]/}"
some nasty   looking  filename
```

```
for f in *.*; do echo --mv "$f" "${f//[\!\*\&\^]/}"; done
```

obviously you can combine these 2
```
$ f='some nasty * & looking ^ !file WS.COM.ext'
$ new=${f//[\!\*\&\^]/}; new=${new/WS.COM/WS}
$ echo "$new"
some nasty   looking  file WS.ext
```
```
for f in *.*; do new={f//[\!\*\&\^]/}; new=${new/WS.COM/WS}; echo mv -- "$f" "$new"; done
```

---

### Post by hateborne on 2013-03-12
That did it. Thank you very much friend.

-Hate

---

