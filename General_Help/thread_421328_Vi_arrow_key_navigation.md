---
title: "Vi arrow key navigation"
date: 2007-04-24
forum: General Help
---

### Post by riksweeney on 2007-04-24
Hi,

Toshiba Satellite M70

I installed Feisty from scratch a couple of days ago and it's mostly OK except for that if I need to edit a file in vi, I can scroll around OK using the arrow keys, but if I then go to insert mode, I can no longer scroll around with the arrow keys and it instead inserts letters such as D. If I then press escape and return to read only mode, I can scroll around again.

Has anyone experienced this and knows what I can do to solve it?

Thanks

Richard

---

### Post by phidia on 2007-04-24
It sounds like the normal behavior of vi although I mostly use vim. When you're in insert mode you can't navigate-you have to press escape to go back to navigation mode. 
If you want to consider using vim there is a interactive tool that teaches how to use it called vimtutor.  sudo apt-get install vim-runtime

---

### Post by taurus on 2007-04-24
```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by riksweeney on 2007-04-24
Thanks for the tips, I'll give these a go later!

---

