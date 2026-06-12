---
title: "vim no X help"
date: 2008-01-29
forum: General Help
---

### Post by madsteer on 2008-01-29
Hello all.  I have vim-full installed on my feisty system.  When I connect to the system via ssh from a terminal that can't support X, typing ... ```
vi file
``` ... causes quite a long hang before I actually get to edit the file, and after I'm done I see ... ```
connect 0 port 6000: Operation timed out
``` ... above the prompt.

Simply typing ...```
vi -X file
``` ... instead removes delay.

My question is, is there a .vimrc entry or something I can put in place to default the "-X" option?  I could create an alias, but that seems kludgy.

Thanks for the help.

---

### Post by mlissner on 2008-01-29
I think use an alias...that is what they're for after all.

You might be able to put it in your sshrc file, or something of that sort though so that it only goes into effect during ssh sessions.

---

### Post by darkkith on 2008-01-31
Check out the 'exclude' option here [http://www.vim.org/htmldoc/options.html#'clipboard']("http://www.vim.org/htmldoc/options.html#'clipboard'")

---

### Post by PinkFloyd102489 on 2008-01-31
I find that nano is easier to use and it runs a lot faster. Maybe try that?

---

### Post by darkkith on 2008-02-01
nano is considerably easier, however, infinitely inferior to vim

---

### Post by madsteer on 2008-02-05
Thanks so much for all the reply's (well not so much on the "use nano" replies.  :)).  Putting this in ~/.vimrc worked: ```
set cb=exclude:xterm.*
```  Basically it's turning off clipboard for terminals that start with > xterm

Thanks darkkith!

---

