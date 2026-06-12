---
title: "Vim indent not working"
date: 2005-06-30
forum: General Help
---

### Post by gdboling on 2005-06-30
I *really* want to learn how to use Vim really well.  I hear from friends it is quite powerful.  Anyway, so I start messing around with it today and it seems that indention of source code is not working.  And niether was syntax highlighting.  I googled for an hour looking things up and read parts of the Vim manaul.  I noticed I have 2 locations:

/etc/vim - only has a vimrc file.  (not .vimrc)
/usr/share/vim/vim63/ - contains a ton of files including ftplugin folder and indent folder with .vim files for a ton of languages.

I edited the /etc/vim/vimrc file to turn on syntax highlighting but I cannot for the life of me get indention to work.  I tried creating a .vim and a .vimrc folder in my home folder and placing appropriate files and folders in there but that doesn't work either.

I talked to a friend of mine that uses vim and he said it tends to be different on different dostros.  Can someone either give me a step by step on getting indention to work or point me to a link that tells me how to for Ubuntu or equevalant distro?

Thanks.

---

### Post by ltmon on 2005-06-30
Try the following whilst in vim command mode:

:set autoindent

If you like it then add the following to your .vimrc

set autoindent

There's so many options available for this that I won't try to list any now.  Browse around the tips and tricks section of [www.vim.org](www.vim.org) to get a real handle on it.

Cheers,

L.

---

### Post by rosslaird on 2005-06-30
Have you tried over at [www.vim.org](www.vim.org), in the tips area?

Indenting takes all kids of forms under vim, so it may not be a configuration issue. There are various "types" of indenting under vim.

Try this page:

[http://www.vim.org/tips/tip_search_results.php?keywords=indent&order_by=rating&direction=descending&search=search](http://www.vim.org/tips/tip_search_results.php?keywords=indent&order_by=rating&direction=descending&search=search)

Ross

---

