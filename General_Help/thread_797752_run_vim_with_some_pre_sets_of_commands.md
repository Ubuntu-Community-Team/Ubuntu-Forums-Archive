---
title: "run vim with some pre sets of commands"
date: 2008-05-17
forum: General Help
---

### Post by amin_inb on 2008-05-17
Hi

is it possible to run vim from terminal with some pre sets of commands ?


I want to open file with vim and apply :set number & :set ruler

some thing like this

$vim myfile.extension :set number & :set ruler

---

### Post by nick_h on 2008-05-17
The syntax is:
```
vim "+set number" "+set ruler" myfile.extension
```
For more details type:
```
man vim
```
Alternatively you could place the presets in your .vimrc file.

---

