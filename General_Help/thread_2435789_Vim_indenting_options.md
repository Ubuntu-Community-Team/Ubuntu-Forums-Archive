---
title: "Vim indenting options"
date: 2020-01-26
forum: General Help
---

### Post by howardsmiller on 2020-01-26
The last few versions of Ubuntu have had a version of the Vim editor that has automatic indenting (I assume based on file type) enabled by default. Without wishing to get into a huge rant, this is always a bad thing (IMO) because it imposes somebody else's idea of indenting style and is therefore almost always wrong and/or useless.

I've spent a long time trying to switch the thing off. I forget now but I've tried all sorts of settings and suggestions. 

Has anybody discovered a *definitive* way of killing automatic indenting?

---

### Post by TheFu on 2020-01-26
Google with a 3 word search "vim disable indentation"

[https://vim.fandom.com/wiki/How_to_stop_auto_indenting](https://vim.fandom.com/wiki/How_to_stop_auto_indenting)
```
cd /usr/share/vim/vimXY   # XY is the number of the vim version on your system.
cp indent.vim indent.vim.bak
```

Indentation will not work anywhere.  There are more selective methods and with an advanced-beginner skill, you could do it on a project/directory or specific file-type basis.

---

