---
title: "HOWTO: Latex WYSIWYG with Vi/Vim and Evince"
date: 2007-11-16
forum: General Help
---

### Post by aschiller on 2007-11-16
Vim is excellent for composing latex documents, and learning how to use all of the editor's will make your work a good 30%-50% (in my experience) faster than using a no-frills editor like gedit.

This short how-to will show you how to make editing .tex files much faster by **automatically saving, compiling, and displaying the latest version of your tex document** every time you make a change.

[SIZE="4"]What You Need:[/SIZE]
[LIST]
[*]A working knowledge of vim.
[*]A working knowledge of creating documents in latex.
[*]The texlive package.  If you don't already have it, ```
sudo apt-get install texlive
```
[*]The full version of vim.  Ubuntu (Gutsy, at least) ships with vim-tiny by default.  If you're going to be using vim, you might as well have the full package (this gives you things like syntax highlighting).  If you don't already have it, ```
sudo apt-get install vim-full
```
[/LIST]

[SIZE="4"]The Strategy:[/SIZE]
Our strategy is to set options in the ~/.vimrc file that make vim execute commands after either a period of inactivity or a save.  We will make vim:
[LIST=1]
[*]**Compile the File**.  It will act silently and suppress all errors so that your work is seamless.  If compiling fails (i.e. any errors occur), you will not see an error, and you will not see any changes to your PDF until you fix the errors.
[*]**Refresh Evince**.  Evince (the standard Gnome Ubuntu document viewer) will reload your file without stealing focus so that you can keep working.
[/LIST]

[SIZE="4"]What You Do[/SIZE]
[LIST]
[*]Edit your .vimrc file with vim (or your favorite editor, though since you're reading this tutorial, I hope you're comfortable with vim).
```
vim ~/.vimrc
```
[*]Paste the following code into the ~/.vimrc file:
```

""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" for LaTeX files
"""""""""""""""""""""""""""""""""""""""""""""""""""""""
au BufEnter *.tex set autowrite "Save before making PDF"
au BufEnter *.tex set updatetime=1000 "Wait 1000 milliseconds (change if you want to)"
au BufEnter *.tex set makeprg=pdflatex\ -halt-on-error\ %\ >/dev/null "make the pdf file, suppress output, don't do anything if there are errors"

"make the file after specified time of not moving and after every save"
au CursorHold *.tex call UpdateFile()
au BufWritePost *.tex call UpdateFile()

" update function
function! UpdateFile()
    silent make
        silent !evince -w %<.pdf>/dev/null &  "refresh the file in evince.  -w option keeps focus on vim console"
        redraw!       "remove artifacts during saves"
        endfunction

" run evince at runtime"
        au BufRead *.tex silent !evince %<.pdf>/dev/null &

```
[*]Start editing tex documents.  Vim will only execute the commands above if your file has a .tex extension, so don't worry about this messing with other files you work on.  Also, make sure all your tex documents have .tex extensions.
[/LIST]

Good luck editing tex documents!  If any of the steps don't work here, post and let me know how I can help you get started.

---

### Post by MrZehl on 2008-07-09
Nice idea, but it doesn't work for me. Just starting with vim and latex.
So I omit the nececssary knowledge of creating pdf's latex.
Installed vim, latexsuite and tex-live.

I did as you described but evince starts with the message unkown mime type. 
That is probably because no pdf is created. Why not?

Very annoying is that evince keeps popping up full screen. So I can't work in VIM. When I activate VIM... *pop*... full screen evince. What can I do about that?

Using Ubuntu 8.04 AMD64.

---

### Post by MrZehl on 2008-07-10
Okay, I re-installed everything and the preview works, but still that annoying behaviour. I'm not able to use vim fullscreen.

---

