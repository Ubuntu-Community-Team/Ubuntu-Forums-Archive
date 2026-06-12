---
title: "[SOLVED] key mapping in vim"
date: 2007-10-04
forum: General Help
---

### Post by Evilgiraffe on 2007-10-04
I've recently switched my thinkpad T42 from ubuntu to kubuntu and, ever since, the arrow keys have stop behaving properly in vim.  

With ubuntu they would behave normally in either insert or command mode.  In Kubuntu they now only behave as directional keys in command mode.  In insert, up maps to A, down to B, right to C and left to D.

Is there any way to restore their correct mapping?  I've just started a chemistry research project and need to edit a shed load of files in vim so this new behaviour is driving me crazy.
:confused:

---

### Post by por100pre1 on 2007-10-05
Check the settings in:

/usr/share/vim/vimrc

and...

~/.vimrc

---

### Post by Evilgiraffe on 2007-10-08
I've solved this.

Apparently it is caused by the feisty fawn default installation of ViM being vim-tiny rather than the full version, vim-full.

```
sudo apt-get install vim-full
```

It takes up about 27MB but that's a small price to pay for the ability to edit files properly :lolflag:

---

### Post by likuidkewl on 2007-11-21
Thanks! that fixed my issues too!  Only difference was that I was using a full 104 kybd.

---

