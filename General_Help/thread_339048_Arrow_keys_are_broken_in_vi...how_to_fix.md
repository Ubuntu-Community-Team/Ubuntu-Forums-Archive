---
title: "Arrow keys are broken in vi...how to fix?"
date: 2007-01-15
forum: General Help
---

### Post by reuben on 2007-01-15
The arrow keys aren't working for me in vi, in insert mode. I.e. if I open vi, press i, and then press arrow keys, I get letters instead of navigation. How do I fix this?

---

### Post by guice on 2007-01-15
you talking command line? or GUI version? Command line version, the arrow keys have never worked nor will they. You have to use vi's own key commands to move around. Go into command mode and use: hjkl -- H is left, J js down, K is up and L is right.

More VI commands here: [http://www.eec.com/business/vi.html](http://www.eec.com/business/vi.html)

---

### Post by otas on 2008-05-15
Had same problem vith vim.

found:
[http://vim.wikia.com/wiki/Fix_broken_arrow_key_navigation_in_insert_mode](http://vim.wikia.com/wiki/Fix_broken_arrow_key_navigation_in_insert_mode)

Just type:

:set term=builtin_ansi

---

### Post by kerry_s on 2008-05-15
> **guice said:**
> you talking command line? or GUI version? Command line version, the arrow keys have never worked nor will they. You have to use vi's own key commands to move around. Go into command mode and use: hjkl -- H is left, J js down, K is up and L is right.

More VI commands here: [http://www.eec.com/business/vi.html](http://www.eec.com/business/vi.html)


always worked on mine, no matter what vi clone i'm using. i'm currently using the "busybox vi" and the arrow keys work there to.
of course i still use the letters to. :)
#+j/k #+w/l/h gets me there faster than arrows
there's also the good old shift+ G/H/M/L etc...
good to learn all the various ways.

---

### Post by fyo on 2008-05-15
A common reason for this is that Ubuntu defaults to installing vim-tiny and not the full vim.

---

### Post by brettg on 2008-05-15
You can fix that with;

   sudo apt-get install vim-full

---

### Post by th3l0rd on 2008-05-30
'sudo apt-get install vim-full' will install all the vim related package and the dependencies, that includes gnome libs, etc... if you dont use gnome and just want to fix this issue in the text mode you can run :

sudo apt-get install vim-runtime

---

