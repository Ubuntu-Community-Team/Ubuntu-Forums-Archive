---
title: "Does Software Center purge or remove?"
date: 2014-04-30
forum: General Help
---

### Post by Romeu_Tristo on 2014-04-30
Hi,    I'm new to Linux. I've installed it for the first time one week ago so my knowledge about it is still very basic.

I have a question. When I'm using the Software Centre to uninstall software, is the command it uses "*purge*" or "*remove*"? And is there a way to change that? By default, I would like it to use "*purge*".

Thanks in advance for any help

---

### Post by vasa1 on 2014-04-30
IMO, it removes. So system config files are still there.

If you want to purge things, it may just be easier to use the command-line. I doubt you can change how the software center works.

---

### Post by ibjsb4 on 2014-04-30
Another choice would be a package manager with such options.

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

To install:

```
sudo apt-get install synaptic
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by Romeu_Tristo on 2014-04-30
Thanks a lot!

---

