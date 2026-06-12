---
title: "Crossover Office"
date: 2006-10-17
forum: General Help
---

### Post by dontgetshocked on 2006-10-17
Does Ubuntu not support or allow Crossover Office to work or be installed?
Can you run Microsoft Office on this OS?
:rolleyes:

---

### Post by Perfect Storm on 2006-10-17
On crossover Office download page, there's a .deb package. Just double-click it and it will install.

---

### Post by Perfect Storm on 2006-10-17
> **Artificial Intelligence said:**
> On crossover Office download page, there's a .deb package. Just double-click it and it will install.

> Can you run Microsoft Office on this OS?
Yes you can, but for what purpose?

---

### Post by dontgetshocked on 2006-10-20
Unfortunately I have a Database written in Access that I maintain for customers and need to use it. Otherwise no need for anything MS makes.

Thanks,

As a programmer myself I loathe crappy software.

---

### Post by anthro398 on 2006-10-20
Well, the fact is that you can, and I do, run some Office applications under Crossover Office.  See their [Access application page]("http://www.codeweavers.com/compatibility/search?name=access&company=&medal=&date_start%5B1%5D=1&date_start%5B2%5D=1&date_start%5B0%5D=2000&date_start%5B3%5D=0&date_start%5B4%5D=00&date_end%5B1%5D=10&date_end%5B2%5D=21&date_end%5B0%5D=2006&date_end%5B3%5D=9&date_end%5B4%5D=42&search=app") for details on running Access.  The short story is that Access doesn't run.  Instead, I run an entire Windows instance in VMWare with Office installed in it.  I also used to keep a Windows box on the network that I could remote desktop to, but there are more steps that way so it's more of a hassle.

---

### Post by trojanlinux on 2006-10-21
can someone please send me the link for the deb package, i can only find the sh package that doesnt work

---

### Post by Perfect Storm on 2006-10-21
You can find their .deb package on their homepage.

Piracy is not tolerated.

---

### Post by trojanlinux on 2006-10-21
sorry, i still cant find it
when i go to

[http://www.codeweavers.com/beta/cxlinux/download/](http://www.codeweavers.com/beta/cxlinux/download/)

all i see is the sh package

---

### Post by Perfect Storm on 2006-10-21
ah, the beta. There's only .sh (script). But when it gets release, they make a .deb file.


What seems the problem?

---

### Post by shanepardue on 2006-10-21
> **Artificial Intelligence said:**
> ah, the beta. There's only .sh (script). But when it gets release, they make a .deb file.


What seems the problem?
i get stopped when installing beta trial mode also. when running "sudo sh install-crossover-standard-prerelease-6.0.0beta2.sh" it says "The '/home/shane' directory does not belong to you.
Point $HOME to your home directory and try again."

---

### Post by T0MA on 2006-11-13
dont run it as super user, just simply sh ...

---

