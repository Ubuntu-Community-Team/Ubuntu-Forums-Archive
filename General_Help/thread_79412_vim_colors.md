---
title: "vim colors"
date: 2005-10-20
forum: General Help
---

### Post by billiejoex on 2005-10-20
Hi all. I set vim code highliting by setting the option:
```
:syntax enable
```
...during a file editing.
How can I set this option as default? 

Thanks in advance

---

### Post by rmjokers on 2005-10-20
Add the following line to the .vimrc file in your home directory.

syntax on

You can put lots on interesting options there.  See:

[http://www.vim.org/tips/]("http://www.vim.org/tips/")

---

### Post by billiejoex on 2005-10-20
Are you sure? It doesn't work on my Ubuntu. :-\

---

### Post by rmjokers on 2005-10-20
Well, I do know that the ".vimrc" file in your home directory is the configuration file for vim (highlighting works for me).  Have you tried adding any other options to the file to test this?

This is what my config looks like:

" Use Vim settings, rather then Vi settings (much better!).
" This must be first, because it changes other options as a side effect.
set nocompatible " Use VIM settings rather than VI

set backup       " use a backup file
set backupdir=~/.vim/backup
set directory=~/.vim/tmp

set showcmd      " show partially entered comands on status bar

set ruler        " show line, col of cursor
set rulerformat=%55(%{strftime('%a\ %b\ %e\ %I:%M\ %p')}\ %5l,%-6(%c%V%)\ %P%)

set showmode     " show me when i am in insert mode
set autoindent   " keep the previous line's indentation
set nonumber     " show line numbers
set incsearch    " do incremental searches
set hlsearch     " highlight search results
syntax on
set wrap
set nolist
set smarttab
set esckeys      " allow arrow keys while inserting
set tabstop=8
set shiftwidth=2
set showmatch
set ignorecase  " Ignore case in searches
set smartcase   " Ignore ignorecase when pattern contains uppercase

---

### Post by ingrid on 2005-10-20
Hi,

May be your vimrc file is in another directory.
Try to add in /etc/vim/vimrc
! It affect all users !

---

### Post by billiejoex on 2005-10-20
> Hi,

May be your vimrc file is in another directory.
Try to add in /etc/vim/vimrc
! It affect all users !
It works. Thank you very much.

@rmjokers: Useful options. Thank you too.

---

