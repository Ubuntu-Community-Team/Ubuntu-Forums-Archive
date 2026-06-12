---
title: "Wubi questions"
date: 2013-01-30
forum: General Help
---

### Post by Sal74 on 2013-01-30
Hello folks,

Is there a way to install Pear Linux OS using Wubi? If yes, could you please let me know how?

Thank you very much for your help.

---

### Post by Mark Phelps on 2013-01-30
Probably not -- as Wubi stands for Windows UBuntu Installer -- which is specific to Ubuntu, not a generic version for other Linux distros.

---

### Post by Sal74 on 2013-01-30
Even if Pear Linux OS is a Ubuntu based distro?

---

### Post by Frogs Hair on 2013-01-30
Yes

You could run it in vm ware or vbox.

---

### Post by offgridguy on 2013-01-30
> **Sal74 said:**
> Even if Pear Linux OS is a Ubuntu based distro?
I don't think pear linux is ubuntu based.

Okay i see i was wrong.

[http://distrowatch.com/table.php?distribution=pear](http://distrowatch.com/table.php?distribution=pear)

And i have an install CD coming from ebay, should be here any day.

---

### Post by bcbc on 2013-01-31
Wubi is compiled with a hard list of options. As mentioned, it only supports Ubuntu and a selection of supported flavours, but there are other variants of Wubi out there, e.g. Mint4Win. There's nothing to stop someone changing the source and recompiling to support a new flavour. Obviously this would be a pain for most people so it's impractical.

There is a way to trick Wubi into installing an unsupported version of Ubuntu or derivative provided it has the same Ubiquity installer. Again there is some expectation that a package (lupin-support) is on that ISO and in most cases I'd guess it won't be. So another workaround is required. It's still a pain and impractical for most, but it's less work than modifying and recompiling the source. e.g. [http://ubuntu-with-wubi.blogspot.ca/2012/10/tricking-wubi-installing-xubuntu.html](http://ubuntu-with-wubi.blogspot.ca/2012/10/tricking-wubi-installing-xubuntu.html)

For all the effort you'd go through it's better to do a normal dual boot.

---

