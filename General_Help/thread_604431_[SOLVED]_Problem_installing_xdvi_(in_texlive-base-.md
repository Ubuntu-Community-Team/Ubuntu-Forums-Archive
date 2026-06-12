---
title: "[SOLVED] Problem installing xdvi (in texlive-base-bin)"
date: 2007-11-06
forum: General Help
---

### Post by jazzgossen on 2007-11-06
After upgrading to 7.10, xdvi doesn't work anymore for me. I get the following result when I try to run it:

```
~> xdvi
Can't exec "xdvi.bin": No such file or directory at /usr/bin/xdvi line 90.
xdvi: xdvi.bin terminated abnormally: -1

```

From what I can see, xdvi should be in the package texlive-base-bin.
I tried reinstalling texlive-base-bin, but it still doesn't work. The package does provide /usr/bin/xdvi, which tries to run xdvi.bin, but xdvi.bin is not supplied with the package. What can I do?

---

### Post by jazzgossen on 2007-11-06
Strange. Previously I used aptitude to reinstall texlive-base-bin. Now I tried doing it using synaptic, and then it worked.

---

### Post by kakk on 2008-01-11
strange, xdvi does not work for me either and reinstalling/configuring texlive-base-bin does not help. 

There is a script /usr/bin/xdvi which executes /usr/bin/xdvi.bin which is link to /etc/alternatives/xdvi.bin which is a link to nonexisting /usr/bin/xdvi.real

and no real executable for xdvi, anyone could explain, why so much linking without the actual program???

xgdvi does not work well either, for some reason. Evince shows me my dvi files, but I would not like to reconfigure auctex for this and evince is slower than xdvi anyway

I'm running 7.10 x86 if that matters.

Regards,
Andres

---

### Post by kakk on 2008-01-12
Ok, it is indeed a bug [https://bugs.launchpad.net/ubuntu/+source/texlive-bin/+bug/156628](https://bugs.launchpad.net/ubuntu/+source/texlive-bin/+bug/156628)

and simple solution that worked for me is:

sudo update-alternatives --auto xdvi.bin

---

