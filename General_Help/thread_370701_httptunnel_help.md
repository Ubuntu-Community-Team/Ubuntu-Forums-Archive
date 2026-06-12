---
title: "httptunnel help"
date: 2007-02-26
forum: General Help
---

### Post by manutdfan2850 on 2007-02-26
Hey, I installed httptunnel from Synaptic, but I need help configuring it and making it work. 

I can't even seem to locate where it was installed to run the program or anything.

here is the site of the program, its FAQ section is not very helpful to me: [http://www.nocrew.org/software/httptunnel.html](http://www.nocrew.org/software/httptunnel.html)

Please help me figure out how to run httptunnel

Thanks in advance

---

### Post by manutdfan2850 on 2007-02-26
anyone? 

thanks in advance

---

### Post by arsya on 2007-03-15
Hi,

Okay, I'll try to give you a bit clue about httptunnel.
You said that you already installed httptunnel from the repository. You already did the first step.
httptunnel package should contain two main binaries:
1. hts --> httptunnel server
2. htc --> httptunnel client

So, the idea is to have a computer (perhaps your home PC) that connected to the Internet. You should run hts in this PC. You could set up your port for httptunnel with hts option.

Than you have your office PC, where it is behind firewall. In this PC you should run htc which point your home PC. You could set up the listening port for your application and the destination address for your home PC with htc option.

After that, you could set the application to use the localhost address and the port (which you configured for htc).

Hope you understand.

---

