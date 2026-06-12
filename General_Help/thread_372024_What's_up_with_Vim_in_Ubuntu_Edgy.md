---
title: "What's up with Vim in Ubuntu Edgy?"
date: 2007-02-27
forum: General Help
---

### Post by spiffytech on 2007-02-27
I've been unable to use Vim in Ubuntu Edgy because it does funny things when I type that older releases didn't do (like put letters when I push the arrow keys). I noticed that Ubuntu Edgy uses Vim 7, rather than the older Vim 6. Is this the problem? Is there a way to reset the keyboard functions to the old style? Nano just doesn't do it for me.

---

### Post by caldevil on 2007-02-27
Something wrong with your .vimrc. My advice is to move your .vimrc to .vimrc.bak and start vim again.

---

### Post by taurus on 2007-02-27
```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by spiffytech on 2007-02-27
"locate .vimrc" returned no results.

Are you suggesting that something has, somewhere along the lines, gone wrong with my Vim configuration? I'm having this problem with a brand-new install if Ubuntu, so that seems odd, unless Canonical changes the .vimrc before shipping Ubuntu.

[EDIT]- Taurus, thank you! That solved my problems!

---

### Post by Jeremy23 on 2007-02-27
I think they did that just to save about 10 megabytes off the install CD by using 'vim-tiny' instead of 'vim'. That sucks, if you ask me.

---

