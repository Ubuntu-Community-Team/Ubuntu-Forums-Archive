---
title: "testing NFS - need persistent writing to disk help"
date: 2018-02-22
forum: General Help
---

### Post by davros-dalek on 2018-02-22
Hi Guys ):P

I'm new to Ubuntu, i haven't played with Linux is a very long time. Anyhow... :popcorn:

I have NFS share setup on some storage (not ubuntu), i have setup a mount point to the storage on the ubuntu server, that all works fine etc etc

What i need to be able to do is continuous write to a txt file or something like that from the ubuntu server to the NFS share so i can monitor what happens when i pull one of the connections to the NFS.

Is there anything i can just download and use or could somebody help out, if it was windows i could do it... :lolflag:

Cheers
davros-dalek

---

### Post by TheFu on 2018-02-22
The type of storage matters.  Not all NFS servers implement all the expected extensions.  

I'd just take some stuff from /dev/random and shovel that into a file for the amount of time you want.  Trivial stuff on Unix systems. Use dd.  Be careful that the of=  points to a file on the NFS that you want.

---

