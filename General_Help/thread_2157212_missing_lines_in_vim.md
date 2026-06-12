---
title: "missing lines in vim"
date: 2013-06-24
forum: General Help
---

### Post by jworr on 2013-06-24
I have an odd problem that I couldn't find an answer to on google.  When I open a file with vim via the command line the first 3 lines are missing.  I have line numbers turned on and the first line is numbered 4.  I can't scroll up either.  However, if I do shift+g then gg I will be at beginning of the file!  It seems that vim's buffer is off with what it is displaying.  Also, if I use gvim, I don't experience any problems.  I'm running 13.04 64bit and I've tried reinstalling and purging vim.  Also I've tried deleting .viminfo without any success.  Any suggestions?  Thanks.

---

### Post by papibe on 2013-06-24
Hi jworr.

My guess would be that there are some control characters in the first lines (binary characters).

Try checking the head of the file with an hex editor, or try this on the terminal:
```
od -a yourfile.txt | head -n 20
```
Let us know how it goes.
Regards.

---

### Post by jworr on 2013-06-25
When I run your command, I see what I expect - the file begins normally.  My problem with vim applies to any file I edit, so I don't think it is an issue with a particular file.  Also gvim works fine on the same files.

---

### Post by rnerwein on 2013-06-25
> **jworr said:**
> When I run your command, I see what I expect - the file begins normally.  My problem with vim applies to any file I edit, so I don't think it is an issue with a particular file.  Also gvim works fine on the same files.
hi
just a feeling - did you have a "vimrc" ????
what's about "vi" ? try it.
ciao

---

### Post by jworr on 2013-06-25
Here is the contents of my .vimrc file:


:set autoindent
:set autochdir
set nobackup
set number
syntax on
set tabstop=3
:set columns=160
:set lines=45
set shiftwidth=2
set tabstop=2
set gfn=Monospace\ 9
:set colorcolumn=80
:highlight ColorColumn ctermbg=lightgrey guibg=lightgrey

---

### Post by jworr on 2013-07-18
I figured out the problem, it is with the line:

:set lines=45

my screen isn't big enough to show that many lines and vim responded by cutting of the top three.  I just changed the line to:

:set lines=30

---

### Post by papibe on 2013-07-18
Glad you worked it out. Thanks for sharing your solution :D

---

