---
title: "How do you get gvim to see current directory?"
date: 2008-01-30
forum: General Help
---

### Post by jsmidt on 2008-01-30
When I open a file outside my home directory with gvim it doesn't see the other files in the directory.  It only looks in home.

For example, when I try to build my file by typing :make, it says there is no makefile.  It only looks for makefiles in the home directory.

How do you get gvim to probe the current directory you are in for files like makefiles?

---

### Post by diaa on 2008-01-30
To change vim(gvim) **current** directory, I use cd, just like the command-line and it works, so ```
:cd Desktop
``` should go to Desktop folder if you are in your home, I'm not really sure it's the right way to do this but it's working fine for me :)

---

### Post by Edward Hou on 2008-04-28
> **jsmidt said:**
> When I open a file outside my home directory with gvim it doesn't see the other files in the directory.  It only looks in home.

For example, when I try to build my file by typing :make, it says there is no makefile.  It only looks for makefiles in the home directory.

How do you get gvim to probe the current directory you are in for files like makefiles?

Try putting ":set autochdir" in your vimrc. It automatically sets the working directory to that of the current file. If that doesn't work, check out this vim tip: [http://vim.wikia.com/wiki/VimTip64](http://vim.wikia.com/wiki/VimTip64)

---

### Post by moogman on 2008-05-18
> **Edward Hou said:**
> Try putting ":set autochdir" in your vimrc. It automatically sets the working directory to that of the current file. If that doesn't work, check out this vim tip: [http://vim.wikia.com/wiki/VimTip64](http://vim.wikia.com/wiki/VimTip64)


Just to clarify this, you need to add the exact text as follows:

```
set autochdir
```

In the file ~/.vimrc (that is, /home/yourusername/.vimrc)

---

### Post by jsmidt on 2008-05-18
> **moogman said:**
> Just to clarify this, you need to add the exact text as follows:

```
set autochdir
```

In the file ~/.vimrc (that is, /home/yourusername/.vimrc)


Thanks, works exactly how I was hoping.

---

