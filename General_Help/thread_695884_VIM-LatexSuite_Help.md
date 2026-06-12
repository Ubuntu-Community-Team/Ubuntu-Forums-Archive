---
title: "VIM-LatexSuite Help"
date: 2008-02-13
forum: General Help
---

### Post by Dougie187 on 2008-02-13
Hey guys, So I am having an issue with vim-latexsuite. I read through all related threads and Didn't get an answer to my problem. Soooo im posting a new one.

For some reason. My Latex-suite isnt working at all. I installed it just simply with a sudo apt-get install vim-latexsuite.

and then proceeded this with a
sudo vim-addons install latex-suite

and now when I open a .tex file with vim, nothing has changed. For example, the :TTemplate command is not working at all, however I do have access to the help files, but they are of little help for my problem.

Any help would be great. Thanks

---

### Post by Dougie187 on 2008-02-14
Any ideas? I know if I source the .vim files the plugin works fine. But I just don't know how to get it to load for the file type. I have filetype plugin on in my .vimrc. But its not helping anything. I have to do a :source /var/lib/vim/addon/ftplugin/tex_latexsuite.vim
or something like that everytime i open a latex document.

---

### Post by Dougie187 on 2008-02-14
I got it. For some reason, my filetype.vim file was set to not recognize .tex documents as latex documents, so I had to add that to the line

```
au BufNewFile,BufRead *.latex,*.sty,*.dtx,*.ltx,*.bbl     setf tex
```


in the file /usr/share/vim/vim71/filetype.vim

The new line read:
```
au BufNewFile,BufRead *.tex,*.latex,*.sty,*.dtx,*.ltx,*.bbl     setf tex

```

---

### Post by seventhc on 2008-02-14
Glad you got it, I was just trying to find more info on it, then noticed you solved it yourself. :D

---

### Post by Dougie187 on 2008-02-14
Heh yeah. It took me long enough. Thanks for the help though!

---

### Post by h20Boodle on 2008-02-16
I think a "better" solution would be to follow the wording in the /usr/share/vim/vim71/filetype.vim file. 

It says:

" Choose context, plaintex, or tex (LaTeX) based on these rules:
" 1. Check the first line of the file for "%&<format>".
" 2. Check the first 1000 non-comment lines for LaTeX or ConTeXt keywords.
" 3. Default to "latex" or to g:tex_flavor, can be set in user's vimrc.

In my ~/.vimrc I added the following line before the filetype detection line (filetype plugin on):


let g:tex_flavor='tex'

After I did that, voila, the filetype was detected properly and the correct menu items showed up in the gvim window when I opened a latex document.

Thanks to the original poster who pointed me to the solution.

---

### Post by AlP on 2008-06-23
ah, nice to see this - will add your post to lp: #225943.

---

