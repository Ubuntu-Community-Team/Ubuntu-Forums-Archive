---
title: "nmap key maps not working with Vim/Cscope"
date: 2013-07-12
forum: General Help
---

### Post by actiononmail on 2013-07-12
Hi,

I am using Vim 7+ plus the cscope to browse the linux Kernel Source Code, over 12.10 Ubuntu. After doing a bit googling I came across the [cscope_mapping.vim]("http://cscope.sourceforge.net/cscope_maps.vim") file which maps several cscope commands under the Vim into shortcut key strokes. I installed that as a  Vim plugin and verified keystrokes using ":nmap" on Vim editor.However none of the keystrokes are working on Vim :???::???::???:. For example I got one of the mapping as 

```
nmap <C-\>e :cs find e <C-R>=expand("<cword>")<CR><CR> 
```

I have tried numerous time by pressing keystroke [CTRL]+[\]+e but all in vain. Anybody got a clue?

Thanks Alot.

---

