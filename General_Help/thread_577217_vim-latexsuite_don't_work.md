---
title: "vim-latexsuite don't work"
date: 2007-10-16
forum: General Help
---

### Post by blurp on 2007-10-16
I am using Gutsy Gibbon with:
[LIST]
[*]vim-full-1:7.1-056+2ubuntu2
[*]vim-common-1:7.1-056+2ubuntu2
[*]vim-doc-1:7.1-056+2ubuntu2
[*]vim-gnome-1:7.1-056+2ubuntu2
[*]vim-gtk-1:7.1-056+2ubuntu2
[*]vim-gui-common-1:7.1-056+2ubuntu2
[*]vim-runtime-1:7.1-056+2ubuntu2
[*]vim-tiny-1:7.1-056+2ubuntu2
[*]vim-latexsuite-20060325-3
[/LIST]

At first, the vim-latexsuite menus in gvim do not launch at all whenever I open a .tex file. I had to add the following to .vimrc to make it work:
```

set runtimepath+=/usr/share/vim/addons/

```

Then, whenever I try to compile a LaTeX file with "\ll", I get the following errors:
```

Error detected while processing function Tex_RunLaTeX:
line    7:
E121: Undefined variable: s:target
E15: Invalid expression: s:target
line   10:
E121: Undefined variable: s:target
E116: Invalid arguments for function Tex_Debug
line   12:
E121: Undefined variable: s:target
E116: Invalid arguments for function Tex_GetVarValue('Tex_FormatDependency_'.s:t
arget) != ''
E15: Invalid expression: Tex_GetVarValue('Tex_FormatDependency_'.s:target) != ''

line   21:
E121: Undefined variable: dependency
E116: Invalid arguments for function Tex_Debug
line   25:
E121: Undefined variable: dependency
E116: Invalid arguments for function Tex_Strntok(dependency, ',', i) != ''
E15: Invalid expression: Tex_Strntok(dependency, ',', i) != ''
line   51:
E121: Undefined variable: initTarget
E15: Invalid expression: initTarget

```

This happens in both vim and gvim.

How do I solve this?

---

### Post by glennric on 2007-10-22
I am having the same problem.  Has anyone been able to fix this?

---

### Post by glennric on 2007-10-22
I figured this out finally.  The problem is in the file /usr/share/vim/vim71/debian.vim.
This is where the variable "runtimepath" is set.  In that file you will find

```
set runtimepath=~/.vim,/var/lib/vim/addons,/usr/share/vim/vimfiles,/usr/share/vim/vim71,/usr/share/vim/vimfiles/after,/var/lib/vim/addons/after,~/.vim/after
```

It should be

```
set runtimepath=~/.vim,/usr/share/vim/addons,/usr/share/vim/vimfiles,/usr/share/vim/vim71,/usr/share/vim/vimfiles/after,/usr/share/vim/addons/after,~/.vim/after
```

I changed this and it works like it should.

Edit:  Actually I found a better solution on launchpad.
[https://bugs.launchpad.net/ubuntu/+source/vim-latexsuite/+bug/137205]("https://bugs.launchpad.net/ubuntu/+source/vim-latexsuite/+bug/137205")

Install the package vim-addon-manager and type
```
 sudo vim-addons -w install latex-suite
```

---

### Post by blurp on 2007-11-13
yup. i used the vim-addons-manager and it worked like magic.

---

### Post by murataht on 2007-11-21
Yes, the everything works.
BUT, when I want to launch the xdvi to view the dvi file, vim do nothing.
it says: ":silent! call Tex_ViewLatex()" and do nothing.

I tried to add the "let g:Tex_ViewRule_dvi = 'xdvi' ", inside .vimrc flle, but it didn't help either.

so, anybody knows about that?

thanks.

---

### Post by murataht on 2007-11-21
sorry to post the question again.
but does anybody has any idea? thanks.

---

### Post by Dougie187 on 2008-02-13
For some reason. My Latex-suite isnt working at all. I installed it just simply with a sudo apt-get install vim-latexsuite.

and then proceeded this with a
sudo vim-addons install latex-suite

and now when I open a .tex file with vim, nothing has changed. For example, the :TTemplate command is not working at all, however I do have access to the help files, but they are of little help for my problem.

---

### Post by fredjoha on 2008-03-13
It doesn't work at all for me either. I install vim-addons and latexsuite with my Synaptic Package Manager. Then I type

vim-addons install latex-suite

Then it should work, right? Wrong, I get this error message when I open a .tex file in my gvim:

$ gvim /tmp/test.tex
Error detected while processing /var/lib/vim/addons/plugin/remoteOpen.vim:
line   37:
E174: Command already exists: add ! to replace it
line   38:
E174: Command already exists: add ! to replace it

I also don't get the extra Tex-Suite menu that I am supposed to get in my gvim.
Anybody knows what's going on here? Thanks for any help!

---

### Post by urgnom on 2008-03-15
The strangest thing about that: if you launch gvim from the terminal, it works. If you open gvim by clicking a tex-file (I've associated .tex with gvim), it does not work. Because of this thing I usually work without the gui stuff...

---

