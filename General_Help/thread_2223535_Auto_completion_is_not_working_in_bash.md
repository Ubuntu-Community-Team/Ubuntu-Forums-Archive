---
title: "Auto completion is not working in bash"
date: 2014-05-11
forum: General Help
---

### Post by s.sariya_work on 2014-05-11
Hello Members,
Looks like I have screwed something that has stopped autocompletion in my system.

I have un commented below from /etc/bash.bashrc
```

if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi


```
and the same is commented at ~/.bashrc

```
source /etc/bash.bashrc
source ~/.bashrc
```

Still, I am having issues.
Auto completion is not behaving properly when = sign is used. 
Ex:
[COLOR=#ff0000]export PATH=~Doc[/COLOR]
when pressing tab, it becomes [COLOR=#ff0000]export ~/Doc[/COLOR]

M/c details:
Linux, Ubuntu 13.10
64 bit

Please help. :(

---

### Post by jensmaucher on 2014-05-11
Is bash-completion installed?
Do a logout and login again.

---

### Post by s.sariya_work on 2014-05-11
Yes, did both again. Still not helping. 
> **jensmaucher said:**
> Is bash-completion installed?
Do a logout and login again.

---

### Post by jensmaucher on 2014-05-11
Hm, i don't know. Sorry

---

### Post by philinux on 2014-05-13
Here's my bashrc file from a clean install 14.04. [http://paste.ubuntu.com/7457074/](http://paste.ubuntu.com/7457074/)

Maybe try mv yours to .bak and try mine.

Logout then in to test.

And this is my /etc/bash.bashrc

[http://paste.ubuntu.com/7457078/](http://paste.ubuntu.com/7457078/)

---

