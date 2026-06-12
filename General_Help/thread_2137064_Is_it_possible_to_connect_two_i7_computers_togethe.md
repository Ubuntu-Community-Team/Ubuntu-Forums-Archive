---
title: "Is it possible to connect two i7 computers together to work as one?"
date: 2013-04-19
forum: General Help
---

### Post by branko.savic on 2013-04-19
Basically what I want to do is to connect my 2 i7 computers so that they can share resources as if they both where one computer!
Main purpose being video editing and playing chess. (I like to compete in computer chess tournaments online, so the more power the better!)

I have been doing a little research on my own, but I still cant figure out what I need, and how, if even possible to do it?

The only answers I have come to is that I need to connect the computers in some form of a cluster/grid, to make them work together.

Does anyone know if this is even remotely possible, and if so how do I go about accomplishing it?

And if it is possible, can someone please tell me if any program can see all shared resources and take advantage of it, or does it have to be a specific program that is writen just for that purpose?

Anyway, I hope that someone will understan what I am looking for, and can help me!

Thanks in advance!

---

### Post by CatKiller on 2013-04-19
Simply, no.

You can run things on a remote computer easily enough using SSH. Thin clients are nothing new. But setting up a compute cluster is really quite tricky and isn't worth it for two nodes.

---

### Post by branko.savic on 2013-04-19
> **CatKiller said:**
> Simply, no.

You can run things on a remote computer easily enough using SSH. Thin clients are nothing new. But setting up a compute cluster is really quite tricky and isn't worth it for two nodes.

Well, I have to start somewhere, and those 2 computers is what I have to work with right now, now if this is doable (and I really want to learn) then I will for sure get more then 2 nodes!

---

### Post by CatKiller on 2013-04-19
The phrase you're looking for, then, is high-performance computing. Although most implementations tend to be custom jobs there might be sufficient information on a particular project to let you follow what they've done. I doubt it will be as simple as just installing a package, though.

I do recall reading about someone making a cluster out of Raspberry Pis fairly recently. The home-brew nature of that project might mean that there's some information available.

---

### Post by philinux on 2013-04-19
> **branko.savic said:**
> Well, I have to start somewhere, and those 2 computers is what I have to work with right now, now if this is doable (and I really want to learn) then I will for sure get more then 2 nodes!

What you need is one of these. 

[http://ubuntuforums.org/showthread.php?t=2136079](http://ubuntuforums.org/showthread.php?t=2136079)

---

### Post by efflandt on 2013-04-19
Linux **cluster** was developed long before **cloud** became a popular term. [https://computing.llnl.gov/tutorials/linux_clusters/](https://computing.llnl.gov/tutorials/linux_clusters/)

Or web search "linux cluster".

---

### Post by branko.savic on 2013-04-19
> **efflandt said:**
> Linux **cluster** was developed long before **cloud** became a popular term. [https://computing.llnl.gov/tutorials/linux_clusters/](https://computing.llnl.gov/tutorials/linux_clusters/)

Or web search "linux cluster".

Very interesting read, but I am interested to get this working on a much smaller scale :)
Is there a simple guide or something to follow on how to get this going in a small network of 2+ computers?

---

### Post by pqwoerituytrueiwoq on 2013-04-19
benefiting from a cluster setup takes some special types of work, this is due to the latency and transfer speeds on a network
here is a old ubuntu cluster guide:
[https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide](https://wiki.ubuntu.com/EasyUbuntuClustering/UbuntuKerrighedClusterGuide)
you could use 2 i7s in one computer with a extremely high end motherboard
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131817](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131817)

---

