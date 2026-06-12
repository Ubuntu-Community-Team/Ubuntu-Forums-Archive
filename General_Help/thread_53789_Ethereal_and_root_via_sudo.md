---
title: "Ethereal and root via sudo"
date: 2005-08-02
forum: General Help
---

### Post by tsteuerwald on 2005-08-02
Hi all,

I'm new here and at first would like to say: "Thanks for the best debian based home user distribution! Very good work!"
But now to my question. I daily use ethereal. It is a network protocol analyzer. To log the network traffic, I must be root. After this, I analyze the packets in ethereal as common user.  So I change to root via sudo, but I wonder, configuration files of the root sessions will be read and saved from/to my user home directory. This is not only really uncomfortable, because after one time using ethereal as root, I can't read my config files as user anylonger (they are after this owned by root). It is also a security hole, as corrupt config files in my home directory can do anything with ethereal in a root session.
Is this a well known issue or do I simple misunderstand the sudo mechanism?

Cheers,

Timo

---

