---
title: "Choosing proper, third party software(e.g. from magazine), installation directory(?)"
date: 2007-11-18
forum: General Help
---

### Post by offline on 2007-11-18
When installing a program(or a version of) that is not in the repositories, for example a program found in cover discs of magazines, which is the proper good practice: just to let it install to "some" directory automatically as it is pre-configured(as I understand) by the developer or is there a way to push it to some proper directory using command line?

For example, the OOo v. 2.3 which I installed will run when I enter:

```
/opt/openoffice.org2.3/program/soffice
```

So, is OOo2.3 binary is in /opt . That probably was not the case for the repository version which I uninstalled. Why did they choose /opt?

Another thing is because I am experiencing(learning) bash and scripts I followed the advice and put my example scripts in a directory(bin) I made in /home/user and used $PATH to make this bin be known by my system as containing binaries. The same method is right for third party programs(packages from mags, sites) too?

---

### Post by p_quarles on 2007-11-18
Did this CD use an installer, or was this just an executable? 

In any case, when you use the package manager, or install from source code, the executable will usually be placed in 
```
/usr/bin
```
That directory is one of the default executable paths, so executables placed there will run by entering just the file name (i.e., you don't need the full directory path).

---

