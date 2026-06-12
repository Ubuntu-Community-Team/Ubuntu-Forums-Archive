---
title: "&quot;PROMPT_COMMAND='pwd&gt;&amp;8;kill -STOP $$'&quot; ???"
date: 2007-05-13
forum: General Help
---

### Post by ubiqus on 2007-05-13
Hi,
I see subj in my command history - I'm pretty sure I didn't write that. 
The previous command, also not written by me is:

 cd "`echo -e '\057home\057ubiqus\057jboss\055\064\056\060\056\065\056GA\057bin'`"

Maybe this is smth that jboss does? Anybody seen this before?

Thanks

---

### Post by Mr. Swillis on 2008-03-17
This is actually being executed from the "~/.bashrc" script that executes when you login. The commands executed within this script will show up in the .bash_history file of any given user. 

Swill

---

