---
title: "Grep + variables?"
date: 2008-02-22
forum: General Help
---

### Post by NewbieIsMe on 2008-02-22
Hi everyone,

I'm kinda new to working with bash scripts so I hope someone can help. :oops:

So basically, I'm trying to grep a variable, but the term is to be found at the end of the line so I have:

> grep "$variable$"

Unfortunately, it seems to think that the first "$" is the end of string/line. How do I fix this?

Thank you for your time :p

---

### Post by NewbieIsMe on 2008-02-22
(Posted this somewhere else, but I this would be the more correct topic to post it in. Sorry about that :oops:)

Hi everyone,

I'm kinda new to working with bash scripts so I hope someone can help. :oops:

So basically, I'm trying to grep a variable, but the term is to be found at the end of the line so I have:

> grep "$variable$"

Unfortunately, it seems to think that the first "$" is the end of string/line. How do I fix this?

Thank you for your time :p

---

### Post by croto on 2008-02-22
did you try this?

```

grep "\$variable$"

```

---

### Post by yabbadabbadont on 2008-02-22
Are you using bash as your shell?  (meaning you have explicitly invoked it in the script) i.e.  #!/usr/bin/env bash

The only way I was able to get grep to interpret the variable as a wildcard pattern, was to enclose the variable in single tick marks as opposed to quotes.  Here are the results of my test:
```
/home/daffy $ echo $EDITOR
vim
/home/daffy $ grep EDITOR .bashrc
export EDITOR=vim
/home/daffy $ grep "$EDITOR" .bashrc
alias vi='vim'
export EDITOR=vim
/home/daffy $ grep ${EDITOR} .bashrc
alias vi='vim'
export EDITOR=vim
/home/daffy $ grep `echo $EDITOR` .bashrc
alias vi='vim'
export EDITOR=vim
/home/daffy $ grep '$EDITOR' .bashrc
/home/daffy $ 

```
Note that only the last test returned no results.

---

### Post by p_quarles on 2008-02-22
Duplicate threads merged. Please post only one support request per issue. If you decide that you have posted in the wrong area, please ask a staff member to move the thread for you.

---

