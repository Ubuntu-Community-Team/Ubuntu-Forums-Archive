---
title: ".tgz ??"
date: 2004-11-17
forum: General Help
---

### Post by wilhelm on 2004-11-17
can anyone please tell me how to get the stuff out of a .tgz archive ..

---

### Post by duff on 2004-11-17
[QUOTE=wilhelm]can anyone please tell me how to get the stuff out of a .tgz archive ..[/QUOTE]
From the console:
```
$ tar zxvf myfile.tgz
```

---

### Post by sfw5000 on 2004-11-17
a little more explanation, if you are interested... .tgz is a combination of a tar archive and a gzip compressed archive. by default, tar archives put a bunch of a files into a single file (.tar) but do not offer any compression. You can then gzip or bzip the .tar file, which usually results in a .tar.gz file.  The "z" option in the tar command adds gzip compression to the tar archive in one step. in ```
tar zxvf myfile.tgz
```, the "x" option is the extract option, which expands the tar archive, "z" uncompresses it, "v" causes the command to list all the files as it works, and "f myfile.tgz" simply names the target file.

hth,

Sam

---

### Post by wilhelm on 2004-11-17
[QUOTE=duff]From the console:
```
$ tar zxvf myfile.tgz
```[/QUOTE]
 dun want to work :(

gruesum:/home/wilhelm/downloads # tar zxvf back-end0.7.1.4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

maybe the files is stuffed ???

thanks for the replies !

---

### Post by duff on 2004-11-17
hmm... looks like someone gave it a bad name.  what's the output of
```
# file back-end0.7.1.4.tgz
``` 

[QUOTE=wilhelm]dun want to work :(

gruesum:/home/wilhelm/downloads # tar zxvf back-end0.7.1.4.tgz

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors

maybe the files is stuffed ???

thanks for the replies ![/QUOTE]

---

### Post by sfw5000 on 2004-11-17
[QUOTE=duff]hmm... looks like someone gave it a bad name.  what's the output of
```
# file back-end0.7.1.4.tgz
```[/QUOTE]

You could also try it without the "x" -- some times a .tgz file isn't compressed... Not sure if it matters to change the order, like put the x before the z ```
tar xvzf filename.tgz
```

---

### Post by duff on 2004-11-17
[QUOTE=sfw5000]You could also try it without the "x" -- some times a .tgz file isn't compressed... Not sure if it matters to change the order, like put the x before the z ```
tar xvzf filename.tgz
```[/QUOTE]
"x" means extract, not unzip.  So it's either compressed with `compress` (replace `z` with `Z`), bzip2 (replace `z` with `j`), not compressed at all (loose the `z` alltogether), or the file is corrupted.

And order doesn't matter.  You compress an entire tar archive, not the files individually.

---

### Post by sfw5000 on 2004-11-17
Right, sorry -- meant z not x. Thanks.

---

### Post by duff on 2004-11-17
[QUOTE=sfw5000]Right, sorry -- meant z not x. Thanks.[/QUOTE]
hey..it's early  ;-)

---

### Post by jwb on 2004-11-17
[QUOTE=wilhelm]can anyone please tell me how to get the stuff out of a .tgz archive ..[/QUOTE]

Have you tried the Archive Manager?

Applications -> Accessories -> Archive Manager

The command line stuff is great to know. I use it often.

But I'm lazy, so I sometimes just use that clicky-dealie.......

Mouse, yeah, that's it.

:-)

---

### Post by wilhelm on 2004-11-18
[QUOTE=jwb]Have you tried the Archive Manager?

Applications -> Accessories -> Archive Manager

The command line stuff is great to know. I use it often.

But I'm lazy, so I sometimes just use that clicky-dealie.......

Mouse, yeah, that's it.

:-)[/QUOTE]
 it says it is a html doc when i do file <filename>, but i have then downloaded it in zip format so i can actually access it now :)

---

