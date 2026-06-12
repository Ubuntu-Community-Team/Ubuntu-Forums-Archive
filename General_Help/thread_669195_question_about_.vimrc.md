---
title: "question about .vimrc"
date: 2008-01-16
forum: General Help
---

### Post by seventhc on 2008-01-16
I just have a simple question about the vimrc, I want vim optimised for python
and would like to know if anyone here can take a look at my vimrc and tell me if it is good the way it is, or should i make any changes to it.
ands now, the vimrc
```

" All system-wide defaults are set in $VIMRUNTIME/debian.vim (usually just
" /usr/share/vim/vimcurrent/debian.vim) and sourced by the call to :runtime
" you can find below.  If you wish to change any of those settings, you should
" do it in this file (/etc/vim/vimrc), since debian.vim will be overwritten
" everytime an upgrade of the vim packages is performed.  It is recommended to
" make changes after sourcing debian.vim since it alters the value of the
" 'compatible' option.

" This line should not be removed as it ensures that various options are
" properly set to work with the Vim-related packages available in Debian.
runtime! debian.vim

" Uncomment the next line to make Vim more Vi-compatible
" NOTE: debian.vim sets 'nocompatible'.  Setting 'compatible' changes numerous
" options, so any other options should be set AFTER setting 'compatible'.
"set compatible

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark

" Uncomment the following to have Vim jump to the last position when
" reopening a file
"if has("autocmd")
"  au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
"    \| exe "normal g'\"" | endif
"endif

" Uncomment the following to have Vim load indentation rules according to the
" detected filetype. Per default Debian Vim only load filetype specific
" plugins.
"if has("autocmd")
  filetype indent on
"endif

" The following are commented out as they cause vim to behave a lot
" differently from regular Vi. They are highly recommended though.
"set showcmd        " Show (partial) command in status line.
"set showmatch        " Show matching brackets.
"set ignorecase        " Do case insensitive matching
"set smartcase        " Do smart case matching
"set incsearch        " Incremental search
"set autowrite        " Automatically save before commands like :next and :make
"set hidden             " Hide buffers when they are abandoned
"set mouse=a        " Enable mouse usage (all modes) in terminals

" Source a global configuration file if available
" XXX Deprecated, please move your changes here in /etc/vim/vimrc
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif

" enable file type detection
filetype plugin indent on

augroup filetypedetect
" re-set the type even if it was set already, when shebang line 
" says it's BaBar Python executable script
au BufRead * if getline(1) == '#!@PYTHON@' | setlocal filetype=python | endif
au FileType * if expand("<amatch>") == "python" | call BbrPySet() | endif
augroup END

" all settings we must use when editing Python source
function! BbrPySet()
    syntax enable
    setl tabstop=4
    setl softtabstop=4
    setl shiftwidth=4
    setl expandtab
endfunction

map <f2> :w\|!python %<cr>

if has("autocmd")
       autocmd FileType python set complete+=k/path/to/pydiction isk+=.,(
    endif " has("autocmd")
```
If anyone has any suggestions or a better config for me, I appreciate any input.
Thanks

---

### Post by scizzo on 2008-01-16
Well I can only suggest that if you are looking for example .vimrc files you can always look at: [http://www.dotfiles.com/]("http://www.dotfiles.com/")

I find that site very useful when getting ideas for .files

---

### Post by seventhc on 2008-01-16
I have looked there, but my problem is, I am not to sure which one would be best for me. ATM I am looking at about 5 different ones, but really have no idea which one to use.

---

### Post by seventhc on 2008-01-16
And one more question, if I also use gvim do I have to also edit the gvimrc or will the configuration in the vimrc take care of it for me?

---

