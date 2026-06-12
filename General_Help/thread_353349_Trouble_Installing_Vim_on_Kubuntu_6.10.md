---
title: "Trouble Installing Vim on Kubuntu 6.10"
date: 2007-02-04
forum: General Help
---

### Post by ColCommunism on 2007-02-04
Sorry if I'm posting in the wrong place.

I'm having some trouble installing gVim on Kubuntu 6.10.  I've unpacked all the files into a directory, but when I type in "make" in the terminal (with or without sudo), it seems to just go on forever.  Looking at the messages, it appears to be looping.  If anybody has any suggestions, I'd appreciate them very much.

Please ask if you need any additional information.

---

### Post by taurus on 2007-02-04
```
sudo aptitude update
sudo aptitude install vim-full gvim
```

---

### Post by ColCommunism on 2007-02-04
Wow.  That worked perfectly.  Thanks, taurus.

---

### Post by donloveslinux on 2008-07-04
It worked for Kubuntu 8.04 Hardy Heron.  Thanks!

---

