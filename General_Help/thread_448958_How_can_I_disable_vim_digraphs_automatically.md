---
title: "How can I disable vim digraphs automatically?"
date: 2007-05-19
forum: General Help
---

### Post by sectionIV on 2007-05-19
I can turn the "digraph entry with backspace" feature off with ":set nodigraph" after starting vim, but that command doesn't seem to work in ~/.vimrc or /etc/vim/vimrc. Other set commands do work in ~/.vimrc. I'd really like to disable digraph insertion with backspace by default. Any suggestions?

I'm using 6.06 Dapper Drake with vim version 1:6.4-006+2ubuntu6.

Thanks,
Lee

---

### Post by sectionIV on 2007-05-20
Nevermind. I found "set digraph" in one of the plugins was overriding ~/.vimrc.

---

