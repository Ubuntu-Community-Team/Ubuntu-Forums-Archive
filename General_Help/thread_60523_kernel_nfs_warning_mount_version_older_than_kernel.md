---
title: "kernel: nfs warning: mount version older than kernel"
date: 2005-08-28
forum: General Help
---

### Post by dninja on 2005-08-28
Can someone please come up with an answer to why this happens, I've seen loads of people asking about this issue but no one has managed to come up with a way to fix it....

The problem, when I try to mount an NFS share from my FreeBSD box I get the following error in the messages log:

kernel: nfs warning: mount version older than kernel

And that terminal locks up. The anoying this is that it used to work but now doesn't. I've just  re-built my FreeBSD server but not touched my Ubuntu box. I've brought the old exports and permissions files from the old FreeBSD setup across so I don't think I've changed anything on that side.

The closest thing to what sounds like an answer is this:
> 
Just like to mention that I tried all of the above but it only started working when I switched from the nfs-user-server to the nfs-kernel-server 

as taken from [http://www.ubuntulinux.org/support/documentation/faq/nfs-server](http://www.ubuntulinux.org/support/documentation/faq/nfs-server) . Unfortunatly he doesn't say how he actually made the change.

Can anyone help?

---

### Post by dninja on 2005-09-02
[QUOTE=dninja]Can someone please come up with an answer to why this happens, I've seen loads of people asking about this issue but no one has managed to come up with a way to fix it....

The problem, when I try to mount an NFS share from my FreeBSD box I get the following error in the messages log:

kernel: nfs warning: mount version older than kernel

And that terminal locks up. The anoying this is that it used to work but now doesn't. I've just  re-built my FreeBSD server but not touched my Ubuntu box. I've brought the old exports and permissions files from the old FreeBSD setup across so I don't think I've changed anything on that side.

The closest thing to what sounds like an answer is this:


as taken from [http://www.ubuntulinux.org/support/documentation/faq/nfs-server](http://www.ubuntulinux.org/support/documentation/faq/nfs-server) . Unfortunatly he doesn't say how he actually made the change.

Can anyone help?[/QUOTE]
 Just upgraded to Breezy, still the same problem.

I've also tried compiling util-linux from source so that it is linked against the running kernel, still no luck.

---

### Post by dninja on 2005-09-06
Fixed it!

The server wasn't listening for UDP packets. As soon as I turned that on everything magically mounted.

I guess that this is a bug with the linux mount as it freezes rather than timing out. I'll report it to someone.

---

