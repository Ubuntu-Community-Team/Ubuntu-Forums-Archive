---
title: "Bleachbit in ubuntu 16.10 does not clear terminal history."
date: 2016-12-10
forum: General Help
---

### Post by Hewjr100 on 2016-12-10
It did so in ubuntu 16.04, but not in 16.10.  Does anyone know why?

Henry

Ps Did a clean/fresh install of 16.10 and re installed bleachbit.

---

### Post by howefield on 2016-12-10
Just checked it on a 16.10 installation and it works as expected deleting the ~/.bash_history file.

So not sure why it wouldn't work for you, but some tips that you might or might not be aware of.. to prevent a command going into your terminal history type a space with the space bar at the start of the command.

To clear the terminal session history  use

```
history -c
```

To what Bleachbit does simply delete the ~/.bash_history file or remove the file contents with

```
> ~/.bash_history
```

---

### Post by Hewjr100 on 2016-12-10
Ok got it thanks, will use space bar method.

Henry

---

