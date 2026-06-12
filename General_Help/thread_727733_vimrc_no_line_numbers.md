---
title: "vimrc no line numbers"
date: 2008-03-18
forum: General Help
---

### Post by ccaaee on 2008-03-18
I've just installed Gusty and am surprised to see that VIM no longer shows my cursor position (line and row) in the bottom right corner.  I've googled myself to death but to no avail.  Any ideas ???

---

### Post by Athelstan101 on 2008-03-18
It's strange how your vim configuration got into this state, but it looks like something has caused a 'set noruler' option.

You may need open your vimrc config file:
```
$ sudo vi /etc/vim/vimrc
```

Add the following line:
```
set ruler
```

---

### Post by ccaaee on 2008-03-19
Thanks Athelstan101
Unfortunately that didn't work.  My vim version in Gutsy is 7.1 . In a Feisty server next door it's 7.0 and the row,column feature works.  From the documentation it seems like "ruler" should be the one but a "grep ruler /etc/vim/vimrc" on both Gusty and Feisty shows nothing.

---

### Post by Athelstan101 on 2008-03-19
OK, try looking in this file for the 'ruler' option: /usr/share/vim/vimcurrent/debian.vim

---

### Post by ccaaee on 2008-03-22
Thanks Athelstan101 but it still doesn't work
I removed everything vim related and reinstalled vim and vim-common.  This installed a thing called /usr/bin/vim.basic which had to be renamed to /usr/bin/vim and all is now well.  I think the problem had to do with the default vim application being vim.tiny which doesn't seem to know about ruler irrespective of where you put it.
Thanks for your suggestions

---

### Post by der_joachim on 2008-03-22
How does your .vimrc look? It should be in your home directory. I can post mine if you like. I do have a ruler and a few other goodies. ;)

---

### Post by Drate on 2008-04-21
What you were looking for was "set nu" for the vimrc file... btw

---

### Post by scorp123 on 2008-04-21
> **ccaaee said:**
>  I think the problem had to do with the default vim application being vim.tiny which doesn't seem to know about ruler irrespective of where you put it. Exactly. It also doesn't know about syntax highlighting and many other features. What you need is the full set of vim: ```
apt-get install vim-full
```

That should take care of the problem and you'd get a vim with all bells and whistles again.

---

