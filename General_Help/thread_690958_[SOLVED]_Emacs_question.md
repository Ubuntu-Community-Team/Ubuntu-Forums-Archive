---
title: "[SOLVED] Emacs question"
date: 2008-02-08
forum: General Help
---

### Post by dstein on 2008-02-08
I finally decided to learn Emacs, rather than using the Ubuntu Text Editor. I typed 'sudo apt-get install emacs', which installed the program. However, it is not the version of emacs that runs in the terminal. Rather, it opened a window and it is Emacs 22.1.1. While I would probably like to keep this version on my computer, I would truly like to access the version of Emacs that runs in the terminal, not a window, as that is what I will be using at school. Any ideas how to install or open this version? Thanks.

---

### Post by jachymc on 2008-02-08
Hi,

both are the same emacss, in the GUI version, you can just use mouse and some menus.
I'm a vim user, so I can not tell you more. I would just say, there must be either some parameter (try emacs --help) or special command (try to write "emacs<TAB><TAB>" .

---

### Post by dstein on 2008-02-08
Oh nice. Thanks. The parameter is 'emacs -nw', which stands for "no window". Any way to make this the default?

---

### Post by kaens on 2008-02-24
You could set it as an alias - alias emacs='emacs -nw'

---

