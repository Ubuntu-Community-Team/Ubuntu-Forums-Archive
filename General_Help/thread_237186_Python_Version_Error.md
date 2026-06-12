---
title: "Python Version Error"
date: 2006-08-15
forum: General Help
---

### Post by tonyr1988 on 2006-08-15
I'm trying to download a program via apt-get, and I get the following error:

> The following packages have unmet dependencies:
  ibuild: Depends: python (< 2.4) but 2.4.2-0ubuntu3 is to be installed
E: Broken packages

My python version is too new, but if I try to uninstall it via Synaptic, it tells me tons of stuff will be deleted (like Alacarte and other programs I need). I've already installed python2.3 but it didn't change the error message. Is there any way I could get the python package to point to a different version, or switch between two versions of python?

---

### Post by scxtt on 2006-08-15
i'm not entirely sure how ibuild is determining what version you're using, but if it's simply doing something like **python -V** to find out, you might be able to get away w/ pointing /usr/bin/python to your 2.3 install instead of the 2.4 version, since /usr/bin/python is just a symlink to /usr/bin/python2.4 (at least that's the default case for me) ...

try:

1. mv /usr/bin/python /usr/bin/python_backup
2. ln -s /usr/bin/python23 /usr/bin/python

you should get something like:

/usr/bin/python --> /usr/bin/python2.3

---

### Post by tonyr1988 on 2006-08-15
Unfortunately, it still gives me the same error.

Is there a safe way for me to downgrade my python install? Would that mess up programs, just going down .1 version?

---

### Post by scxtt on 2006-08-15
not entirely sure ... i suppose it depends on what programs require features in 2.4 that 2.3 doesn't offer, and i can't answer that ... seems to me to be more of a 'problem' w/ ibuild (why does it **have to** be < 2.4?) ...

---

