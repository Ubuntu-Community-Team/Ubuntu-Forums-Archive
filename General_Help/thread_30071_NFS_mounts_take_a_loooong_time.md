---
title: "NFS mounts take a loooong time"
date: 2005-04-27
forum: General Help
---

### Post by gnutered on 2005-04-27
When running Warty, my laptop mounts my server's (Debian testing) NFS mounts instantly.  When the laptop is running Hoary, it sits and waits, seemingly forever.

I did comparative packet captures, and the difference appears after the GETPORT Call and Reply.  Warty sends an FSINFO (ethereal's term, maybe) and continues on.  Hoary doesn't.

This happens whether the mount happens through the bootup process, or the command line.  Though, if I interrupt it with Ctrl-C, the mount has occurred, and seems to work well.

Any clues?

Tony Lewis

---

### Post by ElvisThePelvis on 2005-04-28
Try:

```
sudo apt-get install portmap
``` 

That fixed my long nfs mount times.

---

### Post by gnutered on 2005-05-01
[QUOTE=ElvisThePelvis]Try:

```
sudo apt-get install portmap
``` 

That fixed my long nfs mount times.[/QUOTE]
 Thanks Elvis,

It fixed it for me too.  Wonder why it's not an installed package by default - at the same level as the mount command.

Tony

---

