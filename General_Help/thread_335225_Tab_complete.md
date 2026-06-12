---
title: "Tab complete"
date: 2007-01-10
forum: General Help
---

### Post by jafenske on 2007-01-10
I recently added a new user to my computer and gave the new user admin prowers.  However the tab complete in the terminal doesn't work... How do I turn it on.  

Thanks

---

### Post by nikhilk on 2007-01-10
Check whether TAB completion is enabled in the new user's .bashrc
If following three lines are present in the .bashrc, uncomment them

#if [ -f /etc/bash_completion ]; then
# . /etc/bash_completion
#fi

---

### Post by jafenske on 2007-01-10
Could you be a little more specific... I tried your suggestions and it did not work.  Thanks

---

### Post by nikhilk on 2007-01-10
Did you source the file after editing?
```
source ~/.bashrc
```

---

### Post by jafenske on 2007-01-13
To do this I run run this in the terminal

```
source ~/.bashrc
```

Does this effect /etc/profile? Is that why I am using the source command.

Why don't I need to use the command

```
source ~/bash.bashrc
```

Thanks

---

