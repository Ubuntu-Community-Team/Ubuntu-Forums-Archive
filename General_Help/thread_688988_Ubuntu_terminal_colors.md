---
title: "Ubuntu: terminal colors"
date: 2008-02-05
forum: General Help
---

### Post by jarthel on 2008-02-05
In my i386 Ubuntu laptop, files are displayed with different colors depending on the extension. like .sh are displayed in cyan.

I just installed Ubuntu 7.10 AMD64 in my other PC and the terminal displays everything in black.

can someone help me? I want colors on file extensions so they are easily distinguish.

thank you.

---

### Post by bodhi.zazen on 2008-02-06
Are you looking for color in ls, 

ls --color=always

If so, you can add that as an alias to ~/.bashrc (it is likely there already but needs to be un-commented)

alias ls='ls --color=always'

---

