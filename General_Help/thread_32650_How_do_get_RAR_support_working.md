---
title: "How do get RAR support working?"
date: 2005-05-08
forum: General Help
---

### Post by denzilla on 2005-05-08
I downloaded RAR following the instructions in the unofficial Ubuntu guide, but I cannot open rar files. Anything I'm missing?

---

### Post by tread on 2005-05-08
Install unrar-nonfree. At least, I think thats all I did .. and the gnome-archive utility (whatever it's called) opened a rar file afterwards.

---

### Post by Sam on 2005-05-08
[QUOTE=denzilla]I downloaded RAR following the instructions in the unofficial Ubuntu guide, but I cannot open rar files. Anything I'm missing?[/QUOTE]
I had problems using RAR with the gnome File Roller, read [this](http://ubuntuforums.org/showthread.php?t=24899), maybe it'll help.


To unrar from the terminal:```
$ unrar e <filename>
```
or to append the archive name to the destination directory:```
$ unrar e -ad <filename>
```

---

### Post by RastaMahata on 2005-05-08
weird, I just apt-get isntalled unrar :S

---

### Post by fishfork on 2005-05-08
I added a bit on this to the [Wiki FAQ](http://www.ubuntulinux.org/wiki/FrequentlyAskedQuestions) the other week. Modify/add stuff to it, please! I think the wikis should be used a lot more generally.

---

### Post by Bartholomaeus on 2005-05-10
[QUOTE=Sam]
To unrar from the terminal:```
$ unrar e <filename>
```
or to append the archive name to the destination directory:```
$ unrar e -ad <filename>
```[/QUOTE]

Thank's a lot for this. It works pretty well.

---

### Post by bored2k on 2005-05-10
One can always use ark or winrar through wine for this. Some [or all] password protected .rars usually crash with file-roller.

---

### Post by denzilla on 2005-05-11
unrar did the trick. Thanks fellas :)

---

### Post by PuleX on 2005-11-30
[QUOTE=denzilla]unrar did the trick. Thanks fellas :)[/QUOTE]

Yeah, unrar worked for me too, while file-roller crashed on the password-protected rar's. Thanks!

---

