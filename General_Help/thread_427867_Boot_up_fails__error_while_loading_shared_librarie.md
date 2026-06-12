---
title: "Boot up fails  error while loading shared libraries"
date: 2007-04-29
forum: General Help
---

### Post by phidia on 2007-04-29
This is the complete error message at boot up or when trying to chroot from one of my other installs:
> /bin/bash: error while loading shared libraries: libtermcap.so.2: cannot open shared object file: No such file or directory


Maybe the install is lunch now but if someone has an idea out of this without re-installing I'd really appreciate it.

I've searched on the error message but can't figure out how to solve it, Thanks for reading :)

---

### Post by phidia on 2007-04-29
The other error messgaes at start up are

> init: rcS main process (2630) terminated with staus 127
init: rc-default main process (2631) terminated with status 127

I'm in my edgy install. I'd like to be hopeful but maybe feisty is just messed up beyond repair.

---

### Post by phidia on 2007-04-30
I guess I'm in for a re-install. I've backed up /etc /var /usr/local & /boot I hope that's enough.  Home is on separate partition.

---

### Post by andrikos on 2007-07-09
If someone still has the problem with libtermcap i have to suggest this simple solution 

sudo ln -s /lib/libncurses.so.5 /lib/libtermcap.so.2

Ncurses also works as a wrapper for the old termcap. It worked for me in another program i needed to run.

---

