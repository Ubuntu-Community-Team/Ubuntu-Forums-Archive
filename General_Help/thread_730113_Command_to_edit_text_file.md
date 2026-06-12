---
title: "Command to edit text file"
date: 2008-03-20
forum: General Help
---

### Post by metricben on 2008-03-20
I am trying to edit a small bit of the *.thunarrc* file and want a command that can easily change one variable.  I am using this to enable show hidden files and disable it within a fluxbox menu command.

Basically i want an easy way to change the line:
```
LastShowHidden=TRUE
```

Into:
```
LastShowHidden=FALSE
```

Without any scripting if possible.

Any help appreciated.
Thanks

---

### Post by dannyboy79 on 2008-03-20
you can use gedit to edit it.

sudo gedit .thunarrc

edit it like in all text editors, save it, and close it. Done.

if you're looking for a way to do it thru the command line without even opening it, well I am sure there's a way but I don't know how.

if you're doing it thru SSH you can use nano. It's a terminal based text editor. very easy to use

sudo nano .thunarrc

when you're done making change, hit ctrl and the x key, this will ask you if you want to save it, hit Y, then hit enter to save it as the same name. Done

---

### Post by metricben on 2008-03-20
lol i know how to use nano and gedit, but was looking for a command as opposed to an app that requires user input.

would **sed** do it?

---

### Post by spupy on 2008-03-20
"Without scripting"? How else then? ;)
**sed** would do it:
```
sed -i 's/LastShowHidden=TRUE/LastShowHidden=FALSE/' .thunarrc
```

Why don't you just press Ctrl+H in Thunar?

---

### Post by metricben on 2008-03-21
oh, CTRL-H is too much effort :P

Thanks for reply - it worked perfectly

---

### Post by Trail on 2008-03-21
Academically, 

```
cat document | tr 'LastShowHidden=TRUE' 'LastShowHidden=FALSE' > document
```

should work too, shouldn't it?

---

