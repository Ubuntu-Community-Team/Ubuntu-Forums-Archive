---
title: "gVim crashes upon saving"
date: 2017-01-07
forum: General Help
---

### Post by flex567 on 2017-01-07
When I try to save with the following command gVim crashes. Is there a way to fix that?
It doesn't crashes if I open it with sudo but than all saved files can only be opened by root. 

```
 :w ~/Desktop/hw 
```

this is my .gvimrc file


```
 syntax enable                     "Turn on syntax highlighting. 
filetype plugin indent on             "Turn on file type detection. 

runtime macros/matchit.vim            "Load the matchit plugin.
                        
set showcmd                    "Display incomplete commands.
set showmode                    "Display the mode you are in. 

set backspace=indent,eol,start             "Intuitive backspacing 

set hidden                     "Handle multiple buffers better.
    
set wildmenu                    "Ehanced command line completition.
set wildmode=list:longest            "Complete files like a shell 

set ignorecase                    "Case-insensitive searching     
set smartcase                    "But case-sensitive if expression contains a capital letter


set number                     "Show line numbers.
set ruler                    "Show cursor position.                         
set lines=50 columns=150            "size of window
set guifont=Inconsolata\ 12            "font size?

"Code below is for that you can move the lines up and down with Alt+j and
"Alt+k
nnoremap <A-j> :m .+1<CR>==             
nnoremap <A-k> :m .-2<CR>==            
inoremap <A-j> <Esc>:m .+1<CR>==gi
inoremap <A-k> <Esc>:m .-2<CR>==gi
vnoremap <A-j> :m '>+1<CR>gv=gv
vnoremap <A-k> :m '<-2<CR>gv=gv            
                        
 
```

---

### Post by TheFu on 2017-01-07
Check the file and directory permissions for the file and all your settings.
Often, sometimes, running GUI programs with sudo will create files owned as root, under YOUR HOME.  Find those files and either delete them or chown them to your userid.

In short, **don't use** sudo with GUI programs.  If you want to edit files as root, use **sudoedit** as the command. This is safe.

---

### Post by flex567 on 2017-01-07
One another thing, if I go to shell and run gvim from the shell via for example 
```
gvim new_file
```
I don't have such issues, but if I run it from the launcher (on the left side) then I get issues mentioned above.

---

### Post by TheFu on 2017-01-07
Check the permissions for all the files and settings impacted.

I know ZERO about any launcher. Sorry. Don't use those things.

---

### Post by flex567 on 2017-01-08
[ATTACH=CONFIG]273098[/ATTACH][ATTACH=CONFIG]273099[/ATTACH][ATTACH=CONFIG]273100[/ATTACH]

---

