---
title: "Using Corn Shell"
date: 2006-10-31
forum: General Help
---

### Post by Bosonator on 2006-10-31
Hello,

I'm trying to install a piece of software (IDL Data Analysis Package) that was intended to be used on Red Hat Linux. I think I've found a way to install it in Ubuntu Edgy, but it requires installing and using the corn shell (csh). My question is: can someone tell me if the following steps will leave me with csh (rather than bash) as my default shell?

```

sudo apt-get install csh
sudo ln -s /bin/sh /bin/csh

```

I'd like to just use csh for the install, and revert back to bash afterwards. Is that as simple as removing the symbolic link? Thanks!

---

### Post by karlbowden on 2006-10-31
Once the corn shell is installed. Then from a terminal just run:

/bin/csh

And you will then be in a corn 'subshell'. Just type 'exit' or press Ctrl-D to exit and you will be back in bash.

---

### Post by Georges on 2006-12-04
korn shell: apt-get install ksh
c-shell: apt-get install csh

there is nothing like corn shell

Usually you do not have to change anything (no ln -s) as long as the installer is a correct script (with a "#!/bin/ksh" at the beginning)

---

