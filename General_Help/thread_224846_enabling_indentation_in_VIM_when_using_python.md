---
title: "enabling indentation in VIM when using python"
date: 2006-07-28
forum: General Help
---

### Post by jordilin on 2006-07-28
When I open a python file with vim and start coding it does not indent code after the colon ":". I have installed vim-python. Anyone knows how to do it?

---

### Post by hw-tph on 2006-07-28
vim-python is useful for actually scripting vim itself using Python, just so you know. To enable automatic indenting in vim/gvim, some features must be enabled in your personal configuration file. There are lots of different sorts of indenting in vim, but I prefer to use autoindent and smartindent. The filetype must be set too - this happens automatically if you launch (g)vim with a *.py file as argument or you can set it using *:set filetype=python*.

Here is my current ~/.vimrc for reference:
```
set nocompatible
syntax on
set background=light

set showmatch
set ignorecase
set showmode
set ts=4
set sw=4
set autoindent
set smartindent

" Mappings
nmap <C-N> :noh <CR>
```
The keymapping command at the bottom makes all highlighted search matches go away by a simple Ctrl+N keypress.

Since I want the same settings for gvim, I source my .vimrc in my ~/.gvimrc:
```
so ~/.vimrc   " Grab the console vim settings
colo buttercream
set guifont=Bitstream\ Vera\ Sans\ Mono\ 9
```


Håkan

---

### Post by jordilin on 2006-07-28
Thanks hw-tph, :D

---

