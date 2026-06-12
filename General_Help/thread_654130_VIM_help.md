---
title: "VIM help"
date: 2007-12-30
forum: General Help
---

### Post by G-Unot on 2007-12-30
hey guys im on gusty and i just installed it, but i noticed that vim doesnt do auto-indenting or syntax highlighting, how do i turn these features on, cuz on other os vim is already configured to do these things

---

### Post by jken146 on 2007-12-30
You need to edit the file ~/.exrc to include the line
```
set ai sw=4
```
This turns on autoindenting and sets the indent size to the equivalent of 4 spaces.


edit:  Perhaps that shoutld be .vimrc -- .exrc works for vi.

---

### Post by taurus on 2007-12-30
And also make sure you have installed the vim-full package.

```
sudo apt-get update
sudo apt-get install vim-full
```

---

### Post by G-Unot on 2007-12-30
hmm i install vim-full and still no, and even if i use jken's method what about syntaxing?

---

### Post by Joshua Swink on 2007-12-31
> **G-Unot said:**
> hmm i install vim-full and still no, and even if i use jken's method what about syntaxing?

In ~/.vimrc:

```
syntax on

```
Have you tried [dotfiles]("http://www.dotfiles.com/")? Grab one of their .vimrcs. They're pretty good.

---

