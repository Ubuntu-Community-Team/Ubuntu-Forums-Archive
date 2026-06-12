---
title: "VMWare workstation5 &amp; kubuntu"
date: 2005-04-29
forum: General Help
---

### Post by frs-design on 2005-04-29
Hello,

I'm using a kubuntu distribution and i installed VMWare (with some little problems at the beginning but now it rules  :)  ).

I'd like to know if we can create our new virtual machine on a fat32 partition.

In fact, I have a little hard drive with 4 GB for the linux partition (/ and swap) and a 20GB fat32 hard drive where i stock all my documents.

I just want to create my virtual machine on the 20GB hd but i get an error which tell me i don't have right to write it on the HD but I can read and write in this partition...

I tried launching vmware using sudo but the same thing appears ...

One idea ?

Bye.

---

### Post by odix on 2005-04-29
vmware is not able to set permission attributes on fat32 filesystem (nobody can do that :-)), this could be the reason why.

odiX

---

