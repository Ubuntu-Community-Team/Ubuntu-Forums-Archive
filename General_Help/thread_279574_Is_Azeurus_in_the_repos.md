---
title: "Is Azeurus in the repos?"
date: 2006-10-18
forum: General Help
---

### Post by alecjw on 2006-10-18
Is Azeurus in the repositories? If so, what's it called?

---

### Post by hw-tph on 2006-10-18
```
hakan@devon:~$ apt-cache policy azureus
azureus:
  Installed: (none)
  Candidate: 2.4.0.2-0ubuntu2
  Version table:
     2.4.0.2-0ubuntu2 0
        500 http://archive.ubuntu.com dapper/universe Packages
```

You need to enable the Universe repository. Read the wiki for more information on that sort of stuff.


Håkan

---

### Post by alecjw on 2006-10-18
Aha. Thanks.

---

### Post by alecjw on 2006-10-18
Why's it universe when it's GPL? Universe means closed source, doesn't it?

---

### Post by Kateikyoushi on 2006-10-18
Because it is community supported software.

> The rationale used to determine which software goes into which category is based on two factors:

The level of support software development teams provide for a program.

The level of compliance the program has to the Free Software Philosophy.

> "universe" component

The universe component is a snapshot of the free, open source, and Linux world. In universe you can find almost every piece of open source software, and software available under a variety of less open licences, all built automatically from a variety of public sources. All of this software is compiled against the libraries and using the tools that form part of main, so it should install and work well with the software in main, but it comes with no guarantee of security fixes and support. The universe component includes thousands of pieces of software. Through universe, users are able to have the diversity and flexibility offered by the vast open source world on top of a stable Ubuntu core. 

Please note: universe is not enabled by default when you install Ubuntu, you need to turn it on yourself. Canonical does not provide a guarantee of regular security updates for software found in universe but will provide these where they are made available by the community. Users should understand the risk inherent in using packages from the universe component.

[LINK]("http://www.ubuntu.com/ubuntu/components")

---

### Post by mozetti on 2006-10-18
Also, there has been a bug in the repo version of Azureus, and I'm not sure if it's been fixed. The notification windows for Azureus weren't interactive (pressing the "hide"/"details" button(s) didn't do anything, and the window couldn't be removed (easily).

Your best bet is to install straight from the Azureus homepage. There's a "How-To" on here that guides you in installing Azureus the "non-repo" way that works well.

---

