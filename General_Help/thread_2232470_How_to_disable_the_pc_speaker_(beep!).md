---
title: "How to disable the pc speaker (beep!)"
date: 2014-07-02
forum: General Help
---

### Post by ubuserone on 2014-07-02
Hi everyone , using ubuntu 12.04 ,how to disable the pc speaker (beep!) ?
Everytime I press delete button it beeps and at terminal it beeps when I press backspace , any arrow key and on an empty command .


```
:~$ sudo rmmod pcspkr
ERROR: Module pcspkr does not exist in /proc/modules

:~$ sudo modprobe -r pcspkr
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
```

What does it mean ? 
:confused:

---

### Post by xc3RnbFO8P on 2014-07-02
Did you try **amixer set 'Beep' 0% mute**

---

