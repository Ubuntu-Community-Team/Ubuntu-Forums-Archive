---
title: "Error when you first start VIM: E558: Terminal entry not found in terminfo"
date: 2013-02-09
forum: General Help
---

### Post by dborovsky on 2013-02-09
Hi. 

Set editor vim and install vim-rais. I run VIM the first time and at first the message:

E558: Terminal entry not found in terminfo
'gnome-256color' not known. Available builtin terminals are:
    builtin_amiga
    builtin_beos-ansi
    builtin_ansi
    builtin_pcansi
    builtin_win32
    builtin_vt320
    builtin_vt52
    builtin_xterm
    builtin_iris-ansi
    builtin_debug
    builtin_dumb
defaulting to 'ansi'

I understand from the error, file not found terminfo. Who faced this problem and how to solve it? Thank you in advance for your reply.

P.S. Sorry for my english

---

### Post by schragge on 2013-02-09
Try to start vim like this
```

TERM=xterm vim

```

This error means that the terminal name referenced by environment variable TERM is not found in the terminfo database. To see what it is type ```
echo $TERM
``` I guess it'll show *gnome-256color* in your case.

BTW, what terminal emulator do you use?

---

### Post by dborovsky on 2013-02-09
I use terminal that comes with ubuntu. But i installed terminator, and too same error. 

i checked with  echo $TERM. And type is xterm.

---

### Post by dborovsky on 2013-02-09
Very interesting that when I become a super user(sudo -i) and run the editor VIM, it is a mistake not appear. But as soon get out of,  it again.

---

### Post by rnerwein on 2013-02-09
> **dborovsky said:**
> Very interesting that when I become a super user(sudo -i) and run the editor VIM, it is a mistake not appear. But as soon get out of,  it again.
hi
seems there must be something wrong with the environment. check out if there is something like a ".vimrc" or something else in your ~/ . i guess there must be something like this file which is used by vim.
have a look at: man vim  (what does the man page say about a vim rc-file)
sorry i haven't installed vim just using vi.
cheers

---

