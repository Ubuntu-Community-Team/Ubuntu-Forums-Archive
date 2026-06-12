---
title: "Share Home Partition - 2 Ubuntu Installations"
date: 2007-05-28
forum: General Help
---

### Post by mpgarate on 2007-05-28
would it be safe/wise/possible to share a home partition between two installed ubuntu feistys? One is i386 and the other is 64 (im using a amd 64 Dual core) I have three partitions beside swap: 1 for ubuntu i386, 1 for the home forlder of i386, and another for ubuntu 64. My question: can/should I use the home folder partition for BOTH 64 and i386, or could that mess somthing up?

I set it up (only for the i386) using [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by liberalist on 2007-05-29
I am unsure if that would mess anything up, but I don't see why it should (the home partition is **not** a system partition, right?).

---

### Post by hillbilly on 2007-05-29
There could be problems me thinks. 

   Like for e.g. if you are using KDE with different configurations on both system, then config files could get replaced and screw up your configuration for one of the systems. I guess you could set up user specified configuration files for the windows manager or desktop environment, but I think it would be a pain to keep track, especially if you are using a desktop environment. And you could make the same case for different applications that you use.

---

### Post by mpgarate on 2007-05-29
my solution - for files I want to share, like music pictures, documents, goes on a partition, and in each of the default home folders I put a link to these folders. Works like a charm. I can even cd into the links with the terminal!

---

### Post by liberalist on 2007-05-29
> **mpgarate said:**
> my solution - for files I want to share, like music pictures, documents, goes on a partition, and in each of the default home folders I put a link to these folders. Works like a charm. I can even cd into the links with the terminal!

That is indeed a good solution. Thank you very much.

---

