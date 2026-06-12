---
title: "Oracle VM with Ubuntu?"
date: 2007-11-15
forum: General Help
---

### Post by ndefontenay on 2007-11-15
Hi everyone,

Oracle has releases a completely free Virtual Marchine called Oracle VM. Find it here:
[http://www.oracle.com/vitualization](http://www.oracle.com/vitualization)

Has anybody tried this with Ubuntu yet?

I'm planning to install Kubuntu Feisty Fawn (not GG, I don't want additional troubles with bugs on top of my R&D) and try it with Kubuntu. But I'm looking for experiences from others if any.

Thanks in advance.

Nico

---

### Post by ndefontenay on 2007-11-19
Oups. There was a problem with the link

obviously it's [http://www.oracle.com/virtualization](http://www.oracle.com/virtualization)

Apparently nobody has tried it yet anyway.

---

### Post by portabill on 2007-11-19
I tried to put Oracle VM on a Dell laptop to try it out, but I found that it would not boot after the install because the laptop did not have PAE.  I don't have Oracle support, but since its loosely based on Red Hat and Xen, I went to their websites and came up with that PAE is absolutely required.  I don't know if there is a software or hardware workaround, that is beyond me.  I don't know about the dual-booting, didn't try.

Too bad, I wanted to replace Windows SBS on one of our servers with Oracle VM.  :(

---

### Post by burr1545 on 2007-11-28
It requires  2 servers  , the VM boots to a prompt , thats it , then u have to use the manager tool , ( via another server ) to  manage the VM server , Vmachines  can be created via the command line (i think) , i started  to look at it , but work got in the way ;) 

Its not a virtual appliance , as some believe....  im not sure if both servers can be virtualised , but i suppose if the box was beefy enough ....

---

