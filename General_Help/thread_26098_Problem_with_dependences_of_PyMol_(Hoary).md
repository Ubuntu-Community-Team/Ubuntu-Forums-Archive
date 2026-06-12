---
title: "Problem with dependences of PyMol (Hoary)"
date: 2005-04-11
forum: General Help
---

### Post by Biochemist on 2005-04-11
Hello All.

I think there is a problem with the dependennces of the package pymol (which is a molecular visualization tool in python). when i try to install it with "apt-get install pymol"
I get this error message:

"Since you only requested a single operation it is extremely likel
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  pymol: Depends: python (< 2.4) but 2.4.1-0ubuntu2 is to be inst
E: Broken packages"

the problem seems to be that pymol request python <2.4, and hoary installs python 2.4. I dont know if this can be consider as a bug, if so, I will post it in the bugzilla. If it is my mistake, I would preciate help.

Thanks.

Ps. sorry about my english. I'm not a native speaker.

---

### Post by banditff50 on 2005-04-12
I am not sure what that error means as I am new at using apt for package management.  In the meantime it would probably be easiest for you to just download the actual pymol binary and install it yourself.  The process is very simple and well documented.

[http://pymol.sourceforge.net/obtaining.html](http://pymol.sourceforge.net/obtaining.html)

---

