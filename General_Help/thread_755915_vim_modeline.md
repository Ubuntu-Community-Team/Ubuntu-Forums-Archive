---
title: "vim modeline?"
date: 2008-04-15
forum: General Help
---

### Post by ignign0kt on 2008-04-15
Hello,
I know I can set up a .vimrc file for settings, but I would like the settings to be file specific.  I found out I can do this with modeline.  However after enabling modeline, it doesn't work.
I add this to the top of the file
```
//vim:ts=4
```
And nothing happens.  I enabled modeline in the /etc/vim/vimrc file and the /usr/share/vim/vim71/debian.vim file.  What am I doing wrong here?

I'm running Hardy if that matters

---

### Post by hal736 on 2008-04-15
starting a modeline with vim, it has to have whitespace in front of the vim, or be at the first column of the line.  
In other words, get rid of the //

examples: 

  vim:ts=4
vim:ts=4

---

### Post by ignign0kt on 2008-04-15
Ugh, thanks.  And while on the subject, can I enable syntax through  modelines?  adding 'syntax enable' doesn't seem to work, probably because it's not a set command?

---

