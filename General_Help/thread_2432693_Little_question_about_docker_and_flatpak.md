---
title: "Little question about docker and flatpak"
date: 2019-12-06
forum: General Help
---

### Post by zohran on 2019-12-06
Hello, i have question. Many people make container for many application, and i think it's very good idea.

My question: is it possible to make container or flatpak for specifical program, for example for gcc compiler or other cli, or is it impossible ? I think in future, it's important to uniform all.

---

### Post by Frogs Hair on 2019-12-06
Support question, moved to *General Help*.

---

### Post by deadflowr on 2019-12-07
> My question: is it possible to make container or flatpak for specifical program, 
Sure.
Though flatpak's in general are for Desktop-centric applications.

And developers use containers all the time for this type of thing.

---

### Post by TheFu on 2019-12-09
The specific example of a compiler inside a container is problematic, but there are lots of other excellent choices for programs and servers to be run inside a container.  The best practice for any container is 1 program/daemon per container.  These are not full VMs and treating them like a VM is a big mistake.  Inside a container should be 1 program that does what the container is meant to accomplish, nothing extra.   This is for security.

But a compile server does multiple things by default and having a full build environment inside a container would be a hassle. There would be dependent libraries, development tools like gmake, libtool, nm, ar, preprocessors, compilers, linkers, language parsers like lexx and yacc (or bison and flex) and a number of packaging and testing tools.  And version control tools.  Without all the code, for each developer, available, the environment would be less than useful.  And with all those development tools, the 1-program per container philosophy is trashed. There are very good reasons for the 1-program, 1 container method. It is because container security comes mainly by NOT having any other programs available inside the container.  With even a few tools, hackers have been able to break out of every container system and gain access to the host.

In a Unix environment, better to just setup a real compiler server or full VM that the team shares for this stuff.  Breaking out of full VMs has proven to be difficult, though methods have come up about every 4-6 yrs.  The security model of the VM is much better understood and handled.  The price is 10x less VM density to Container density on the same physical hardware.

But containers are really great options for running 1-trick systems.  Just don't fall into the trap of things Container == Virtual Machine.  They are nowhere near similar technologies.

---

