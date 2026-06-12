---
title: "Problem with Unison on AMD64"
date: 2005-05-10
forum: General Help
---

### Post by Londo on 2005-05-10
I've been using Ubuntu on AMD64 for a while now, and for the most part it's been working perfectly, until yesterday I stumbled upon a little problem with the Unison file synchronization / replication software. 

The problem seems to only occur on AMD64 machines - these ones are running on the 2.6.8.1-4-amd64-k8-smp kernel package. So, when I attempt to synchronize a directory over the network, after displaying "Reconciling changes" the program just spits out a "Segmentation fault". I tried the same with a regular 32-bit Warty installation and the synchronization works beautifully. 

I was able to get Unison working by (*gasp*) replacing the /usr/bin/unison executable with a statically linked binary (from [http://www.cis.upenn.edu/~bcpierce/unison/download/stable/unison-2.9.1/unison.linux-static-textui)](http://www.cis.upenn.edu/~bcpierce/unison/download/stable/unison-2.9.1/unison.linux-static-textui)). This is obviously not a fix I'd prefer to use, since I'll have to set the package on hold with dpkg. 

So, any thoughts?

---

