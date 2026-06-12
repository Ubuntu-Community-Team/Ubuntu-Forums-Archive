---
title: "Vim-latexsuite on gvim; Can't get it to work"
date: 2015-12-05
forum: General Help
---

### Post by markodd on 2015-12-05
Hey,

I'm trying to get vim-latexsuite working on gvim. Unfortunately, I can't get it to work.

I've vim, gvim and vim-latexsuite installed. However, when I open a .tex file in gvim, I see no latex-related menus. 

Any suggestions?

---

### Post by steeldriver on 2015-12-05
According to

```
apt-cache show vim-latexsuite
.
.
.
By default, vim-latexsuite is not enabled. Please read /usr/share/doc/vim-
 latexsuite/README.Debian after installing the package.

```

The README.Debian file says

```

Dear user, this package provides the vim addon latex-suite, but it is not enabled
per default. If you want to enable it for your user account execute:
        vim-addons install latex-suite
Similarly, to enable it for all users of this system execute (as root):
         vim-addons -w install latex-suite
vim-addons is provided by the vim-addon-manager package, have a look at its
manpage for more information.

Additionally, you need to add the following lines
 filetype plugin on
 set grepprg=grep\ -nH\ $*
 filetype indent on
 let g:tex_flavor='latex'
to ~/.vimrc (or to /etc/vim/vimrc as root) for full usability.
For more info about this lines, type ":help ls_1" in vim (after enabling this
plugin with vim-addons).

```

It seems to work for me after doing that

---

### Post by martin-sjostrand on 2016-01-22
Adding the information above to .vimrc isn't enough. You'll have to run this command to in a terminal:
```
sudo vim-addons -w install latex-suite
```

That will install the plugin correctly and then the menus will show up.

Reference: [http://andrewbolster.info/2011/10/vim-latex-suite-install-on-ubuntu/](http://andrewbolster.info/2011/10/vim-latex-suite-install-on-ubuntu/)

Worked for me...

---

