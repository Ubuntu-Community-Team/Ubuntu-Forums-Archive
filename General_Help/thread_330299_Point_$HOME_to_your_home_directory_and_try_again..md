---
title: "Point $HOME to your home directory and try again."
date: 2007-01-02
forum: General Help
---

### Post by philetus on 2007-01-02
Someone please explain tjis to me.

Point $HOME to your home directory and try again.

---

### Post by ~LoKe on 2007-01-02
In the terminal, type
> $HOME
It should echo something like...
> loke@x04d:~$ $HOME
bash: /home/loke: is a directory

If not, then let me know.

---

### Post by philetus on 2007-01-02
The '/home/tom' directory does not belong to you.
Point $HOME to your home directory and try again.
tom@tom:~$ $HOME
bash: /home/tom: is a directory
tom@tom:~$  sudo sh install-crossover-standard-demo-6.0.0rc2.sh
Password:
Verifying archive integrity...OK
Uncompressing CrossOver Linux Standard
...................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
The '/home/tom' directory does not belong to you.
Point $HOME to your home directory and try again.
tom@tom:~$

---

### Post by ~LoKe on 2007-01-02
> sudo chown tom:tom $HOME

Give that a shot.

---

