---
title: "gvim is blind about a new plugin"
date: 2007-03-29
forum: General Help
---

### Post by cayamara on 2007-03-29
Hi!

I wanted to do some Ruby on Rails development and decided to do it using gVim and [rails.vim]("http://www.vim.org/scripts/script.php?script_id=1567"). So I unpacked the files to ~/.vim/plugin, but gVim won't let me use any of the commands from that script. Strangely, all this works in the command-line vim and in Cream, which is a more user-friendly configuration of vim, but I don't like it much.

So, why does gVim act that way? Where do I have to put the plugin so that gVim loads it?

Thanks in advance!

Oh, and here is my ~/.vimrc:
```
set nocompatible
syntax on
set number
filetype plugin indent on
set mouse=a

runtime! macros/matchit.vim

augroup myfiletypes
autocmd!
autocmd FileType ruby,eruby,yaml set ai sw=2 sts=2 et
augroup END
```

---

### Post by Railsbuntu on 2007-11-12
Bump. Did you find any solution?

I have the same problem with gvim and matchit.

---

### Post by Banter on 2007-11-18
Bump.

I've spent all morning on the same problem.

---

