---
title: "Vim - Wanna change the highlight color just like Gvim"
date: 2014-12-26
forum: General Help
---

### Post by flaymond on 2014-12-26
Hey guys, I'm using vim as my personal text editor. I found it good and really fun to use(also pretty fast), but I wanna make it more pretty in the highlighting perspective. Is there anyway I can change the vim highlighting color just like Gvim use? or is there any nice theme I can use? 

(GVim highlighting default color is very nice, and easy to see....)

---

### Post by Impavidus on 2014-12-26
Vim running in a terminal can use the colours made available by the terminal, so if you want different colours, you can tweak the palette used by the terminal. Vim just issues a numerical code that causes the terminal to switch colour. It should be possible to change the colours associated with certain syntax elements, but that's a totally different matter.

I don't use gvim.

---

### Post by hal8000b on 2014-12-26
Vim already has some builtin colorschemes.  Open a file to edit with vim, you
will get the default scheme.

Then type:

:colorscheme

(Vim supports tab completion so after : and color press "tab" to complete colorscheme)

then press a space and then press tab, this will cycle through all available schemes on
your system. Pressing enter changes to the colorscheme.

If you want to use a particular colorscheme by default then you can edit /etc/vim/vimrc
colorschemes can be found many places for example:

[http://vim.wikia.com/wiki/Change_the_color_scheme](http://vim.wikia.com/wiki/Change_the_color_scheme)

---

### Post by flaymond on 2014-12-26
Thanks hal! It worked like charm! It's a nice scheme! Impadivus, also thanks..but it not worked....but nevermind, my problem solved :)

---

