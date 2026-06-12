---
title: "vim latex-suite"
date: 2008-03-02
forum: General Help
---

### Post by Manojo on 2008-03-02
Hi,

I used to use vim-latexsuite quite okay so far (combos like \ll working nice for compiling etc.). Then I installed a new c plugin for vim as well as a python plugin. I also had to change my .vimrc. And now, latex doesn't repond to "\ll" compile button .. What to do = 

Thanks,
Sashi

PS : here's my vimrc

syntax on
set nu
set ai
set cindent shiftwidth=4
set backspace=indent,eol,start
set ts=4
set sw=4
set mouse=vn
set nohlsearch

set autowrite
set incsearch
set nowrap

filetype plugin on
"python pimper
au FileType python source /home/manojo/.vim/python.vim
let g:tex_flavor='tex'

---

