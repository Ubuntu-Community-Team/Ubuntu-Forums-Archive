---
title: "enabling gvim syntax highlighting"
date: 2016-05-29
forum: General Help
---

### Post by engine on 2016-05-29
I've downloaded a syntax file for mup source
I've saved the syntax file mup.vim in /usr/share/vim/vim74/syntax
The syntax file is not listed when I use the command "Syntax > Show filetypes in menu"
Triggering "Syntax on/off for this file" just displays 'filetype unknown'

What have I missed, and how do I solve the problem?

Ubuntu 14.04.4, Vim 7.4 Huge

---

### Post by ashwin.kj on 2016-06-01
Hi
If you want the syntax files to be accessible by all users then I think the correct path to save the file is ```
/usr/share/vim/vimfiles/syntax/
``` 
The 'syntax' folder might not exist and will need to be created. 
If you just want it for your own user then you can save it to ```
~/.vim/sytax/
```
Depending on your usage of VIM, in this case, both the folders might need to be created first.
Hope this helps

---

### Post by engine on 2016-06-04
Thanks for the tips. I've now got to the stage where
```
:set syntax=mup
```
applies highlighting to the current file.

No idea how to make it automatic for all .mup files, though.

---

### Post by spjackson on 2016-06-04
> **engine said:**
> Thanks for the tips. I've now got to the stage where
```
:set syntax=mup
```
applies highlighting to the current file.

No idea how to make it automatic for all .mup files, though.

I think you need to add something like the following to /usr/share/vim/vim74/filetype.vim
```

au BufNewFile,BufRead *.mup                setf mup

```

---

