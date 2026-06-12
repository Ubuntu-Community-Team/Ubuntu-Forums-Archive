---
title: "how to remove squid"
date: 2006-11-02
forum: General Help
---

### Post by hartunnoo on 2006-11-02
how to remove squid?

sudo apt-get --purge remove squid

everything is ok. but when I tried to browse internet using my workstation, the page cannot be display :(

porxy in option tools -> connection is set to no proxy

but still failed.

when I reinstalled squid on my server box then everything works. I dont know how to solve this problme.

---

### Post by kidders on 2006-11-02
Hi there,

You must be forgetting to remove a reference to your proxy somewhere. Were you proxying transparently?

Did your internet connection ever actually work *without* squid?

---

### Post by hartunnoo on 2006-11-02
> You must be forgetting to remove a reference to your proxy somewhere. Were you proxying transparently?

I'm not sure but,I assume it is not transparent.

> Did your internet connection ever actually work without squid?

my server box can ping isp and other workstations.

---
After finished fresh installed server ubuntu, I configure my /etc/resolve
/etc/hosts
/etc/network/interface

everything is ok but problem is my workstation cannot go online.

I guess I need to install bind9.. but I'm worry if I installed it then something might worse things happened.

So I just keep on waiting for the good answers.

Thank you.

---

### Post by kidders on 2006-11-03
It sounds like your computers are accessing the internet via a server, which is why I was wondering whether they were ever able to access the web *without* squid. You may have forgotten to configure your server for NAT.

If that's the case, squid was the only reason your internet connection ever worked properly. Am I on the right track? Either way, we'll find the problem quickly :-)

---

