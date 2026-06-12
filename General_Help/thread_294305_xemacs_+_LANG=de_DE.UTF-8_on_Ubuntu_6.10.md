---
title: "xemacs + LANG=de_DE.UTF-8 on Ubuntu 6.10"
date: 2006-11-06
forum: General Help
---

### Post by amel48 on 2006-11-06
Hi,

I can't make xemacs work properly on my fresh installed edgy system. I installed the gnome-mule packages as edgy uses for me de_DE.UTF-8.

But:

I ran /usr/bin/xemacs-21.4.19-gnome-mule without any custumization (i.e. no ~/.xemacs directory)
and typed an "Umlaut a" ä in the scratch buffer. I saved that to an file. od -c gives me:
```
lulu:/home/bav> od -c xxx
0000000   ;   ;       T   h   i   s       b   u   f   f   e   r       i
...
0000300   e   r   .  \n  \n 303 244 344
0000310

```
After some googling I found the advice to have
```
lulu:/home/bav> cat .xemacs/init.el
(require 'un-define)
(set-coding-priority-list '(utf-8))
(set-coding-category-system 'utf-8 'utf-8)

```
So I ran again /usr/bin/xemacs-21.4.19-gnome-mule

and typed my ä "Umlaut a", which SURPRISE gave me TWO ä on the screen.
```
lulu:/home/bav> od -c xxx111 
...
0000300   e   r   .  \n  \n 344 344
0000307

```
Loading the previously saved file gives me two ä on the screen. The modeline says Raw. If I input the Euro-symbol, xemacs says "€ not defnied."

I'm afraid I'm lost here. Any help really appreciated.

Kind regards

Gerd

---

