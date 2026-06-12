---
title: "vim commands don't work?"
date: 2007-05-04
forum: General Help
---

### Post by Kalixa on 2007-05-04
Hello. I have just reinstalled Ubuntu on my harddrive. Before formating I of course did some backups. But I have a problem with my .vimrc backup. Before formatting it worked perfectly. But now I get these errors when opening vim:

line    2:
E319: Sorry, the command is not available in this version: :syntax enable
line   14:
E538: No mouse support: mouse=a

This is my .vimrc file:

" Enable syntax highlighting:
:syntax enable

" Here are my mapped sequences:
:map <space> <c-f>
:map <backspace> <c-b>
" These are used when searching through a document:
:set incsearch
:set ignorecase
:set smartcase
" Set line numbering:
:set number
" Make it possible to use the mouse in all modes:
:set mouse=a
" Spell check can be set by using: :set spell 
" Set smartindention. VIM will find out when to indent AFAIK.
set smartindent

" Set the Tab button to indent four spaces.
set shiftwidth=4
set tabstop=4
set expandtab
set smarttab


So why do I get these errors? It worked perfectly before formatting my computer.

---

### Post by YoG%*@ on 2007-05-04
IIRC, vim is not fully installed when you're doing a fresh install. try aptitude install vim - should fix your problem!

hth,
mux

---

### Post by Kalixa on 2007-05-04
> **mux said:**
> IIRC, vim is not fully installed when you're doing a fresh install. try aptitude install vim - should fix your problem!

hth,
mux

Yes, that worked. Thank you.

---

