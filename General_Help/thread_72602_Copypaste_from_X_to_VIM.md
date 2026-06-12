---
title: "Copy/paste from X to VIM"
date: 2005-10-06
forum: General Help
---

### Post by PMO6022 on 2005-10-06
Does anyone know how to copy and paste from an X application - firefox for example - into vim?  I know about the middle click to copy, and that works for vim to X, but not the other way around.

I've searched the tips at [www.vim.org]("http://www.vim.org") without much luck.  It sure would be nice to be able to copy snippets of code from the web into a file through vim, instead of firing up scite or gedit.

Thanks!

---

### Post by ranf on 2005-10-07
[QUOTE=PMO6022]Does anyone know how to copy and paste from an X application - firefox for example - into vim?[/QUOTE]

I use <Ctrl+Shift+V> in gnome-terminal.

---

### Post by heimo on 2005-10-07
I regularly copy-paste stuff from other X applications to terminal vim, and I think my procedure is something like... 
[LIST=1]
[*][esc]   
[*]:set noai (set autoindentation to off)   
[*]i (go to insert mode) [/LIST] paint text and middle-click on vim.

---

### Post by PMO6022 on 2005-10-07
[quote=ranf]I use <Ctrl+Shift+V> in gnome-terminal.[/quote] 
Great!  That worked.  I don't know why I hadn't tried that before.  Thanks.

---

