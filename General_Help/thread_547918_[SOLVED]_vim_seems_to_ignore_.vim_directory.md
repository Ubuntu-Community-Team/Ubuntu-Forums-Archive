---
title: "[SOLVED] vim seems to ignore .vim directory"
date: 2007-09-10
forum: General Help
---

### Post by doc_solitude on 2007-09-10
Hello all!

Forgive me if this question turns out to be trivial, but right at the moment I am helpless! My problem is, that vim seems to ignore my ~/.vim directory.

I want vim to automatically detect *.txt files and set the file type 'text' for them. According to the vim manual the solution to this is to create a file called 'filetype.vim' under ~/.vim/ftplugin/ with the following content:

```

augroup filetypededtect
    "" Files ending with .txt are text files
    au BufNewFile,BufRead *.txt         setf text
augroup END

```

This worked until last week (in fact I did this last week and only tried it out once, but it worked)! Sometime around the weekend there was an update from vim 7.0-164+1ubuntu7 to 7.0-164+1ubuntu7.2. Today I noticed that setting the file type does not work anymore. 
I already tried to rename the file 'filetype.vim' to 'txt.vim' but that did not help. What am I doing wrong? Does anybody have the same problem?

Related to this problem is, that I am not able to install [latexsuite]("http://vim-latex.sourceforge.net/"). I followed the installation instructions but when opening a *.tex file with gvim the latex mode does not seem to be loaded (i.e. no gui buttons or menu entries relating to latex are shown).

My .vimrc file might be useful information, although it is basically the default .vimrc shipped with vim.

```

" When started as "evim", evim.vim will already have done these settings.
if v:progname =~? "evim"
  finish
endif

" Use Vim settings, rather then Vi settings (much better!).
" This must be first, because it changes other options as a side effect.
set nocompatible

" allow backspacing over everything in insert mode
set backspace=indent,eol,start

if has("vms")
  set nobackup          " do not keep a backup file, use versions instead
else
  set backup            " keep a backup file
endif
set history=50          " keep 50 lines of command line history
set ruler               " show the cursor position all the time
set showcmd             " display incomplete commands
set incsearch           " do incremental searching

" For Win32 GUI: remove 't' flag from 'guioptions': no tearoff menu entries
" let &guioptions = substitute(&guioptions, "t", "", "g")

" Don't use Ex mode, use Q for formatting
"map Q gq

" This is an alternative that also works in block mode, but the deleted
" text is lost and it only works for putting the current register.
"vnoremap p "_dp

" Switch syntax highlighting on, when the terminal has colors
" Also switch on highlighting the last used search pattern.
if &t_Co > 2 || has("gui_running")
  " Tell vim that the terminal background is dark
  set background=dark
  " Choose a colorscheme
  colorscheme elflord
  syntax on
  set hlsearch
endif

" Only do this part when compiled with support for autocommands.
if has("autocmd")

  " Enable file type detection.
  " Use the default filetype settings, so that mail gets 'tw' set to 72,
  " 'cindent' is on in C files, etc.
  " Also load indent files, to automatically do language-dependent indenting.
  filetype plugin indent on

  " Put these in an autocmd group, so that we can delete them easily.
  augroup vimrcEx
  au!

  " For all text files set 'textwidth' to 78 characters.
  autocmd FileType text setlocal textwidth=78

  " When editing a file, always jump to the last known cursor position.
  " Don't do it when the position is invalid or when inside an event handler
  " (happens when dropping a file on gvim).
  autocmd BufReadPost *
    \ if line("'\"") > 0 && line("'\"") <= line("$") |
    \   exe "normal g`\"" |
    \ endif

  augroup END

else

  set autoindent                " always set autoindenting on

endif " has("autocmd")

"" Set default indentation width
set shiftwidth=4


"" Use spaces for indenting only
set expandtab

"" Set the number of spaces a tab counts while editing. When expandtab is 
"" enabled, vim will only insert spaces. Else it will insert a combination 
"" of tabs and spaces in order to reduce the size of a file.
set softtabstop=4

"" Show line numbers
"set number

```

Any help is appreciated!

Thanks in advance, doc.

P.s.: Just in case you didn't notice ;): I'm a total vim newbie! I switched to vim recently.

---

### Post by doc_solitude on 2007-09-11
Hello again :)

Today I noticed, that vim does not really ignore my ~/.vim directory. It just fails to detect any file types.  I found this out by installing latex suite again. As expected gvim didn't show any buttons. After setting the filte type manually (:setfiletype tex) the buttons showed up.
Vim is compiled with +autocmd. So "filetype on" in my .vimrc (see above) should work.
I'm clueless!

cu doc

---

### Post by doc_solitude on 2007-09-11
Hello!

I managed to solve the problem. It was a misunderstanding of the vim help :oops:! 
If you want do detect the type of a file by its name (for example because it ends with *.txt) you must create a 'filetype.vim' file in your '~/.vim' directory.
Putting the following content in it then enables the file type detection:

```

if exists("did_load_filetypes")
    finish
endif
augroup filetypedetect
    au! BufRead,BufNewFile *.txt      setfiletype text
augroup END

```

The solution to the second problem (latex suite does not load automatically) is related to it. The default setting is that vim must look at the content of a *.tex file to determine its file type. As I always tried it with empty *.tex files, the filetype detection failed!

I hope somebody else will profit from my posts!

cu doc

---

