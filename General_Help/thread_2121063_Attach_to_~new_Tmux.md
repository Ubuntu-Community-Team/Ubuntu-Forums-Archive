---
title: "Attach to ~new Tmux"
date: 2013-02-28
forum: General Help
---

### Post by kid1000002000 on 2013-02-28
Is there a command that allows one to start a new Tmux new-window if none exist, or to open a new-session in said window if new-window has already been created? 
My end goal is to be able to cycle through them via c-b p and n.

man page: [http://www.openbsd.org/cgi-bin/man.cgi?query=tmux&sektion=1](http://www.openbsd.org/cgi-bin/man.cgi?query=tmux&sektion=1)

---

### Post by dcstar on 2013-03-01
> **kid1000002000 said:**
> Is there a command that allows one to start a new Tmux new-window if none exist, or to open a new-session in said window if new-window has already been created? 
My end goal is to be able to cycle through them via c-b p and n.

man page: [http://www.openbsd.org/cgi-bin/man.cgi?query=tmux&sektion=1](http://www.openbsd.org/cgi-bin/man.cgi?query=tmux&sektion=1)

You mean like the **list-sessions** and **target-session** commands that the man page explains?

---

### Post by kid1000002000 on 2013-03-01
I'm having trouble interpreting the man page, so thank you for replying. I am trying to migrate to tmux from screen.

Currently, I have bash scripts invoked via **screen -d -m /path/to/script**. The scripts can be hooked into by simply opening a terminal and issuing **screen -r**. What I am trying to do is review all of these scripts with the unknown tmux commands and cycle through them via **c-b p**. I don't know how to code this.

---

### Post by markbl on 2013-03-02
Not exactly sure what you are after but just add
```

new-session

```
to the end of your ~/.tmux.conf.

Then just always type "tmux a" to attach to an existing session, or start a new one if there aren't any.

---

