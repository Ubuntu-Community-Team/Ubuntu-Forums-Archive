---
title: "Can anyone install debs from an nfs share?"
date: 2008-04-04
forum: General Help
---

### Post by MountainX on 2008-04-04
I have an nfs share that is working correctly. I have some deb packages stored on the nfs server that need to be installed on client Ubuntu machines. I tried for the first time to install (using GDebi) and the installer crashed repeatedly. When I copied the debs to the local HDD, the installer worked. Is this normal? (I haven't been using Linux for long.)

---

### Post by MountainX on 2008-04-07
If you are able to install debs from an nfs share, please reply here. 

I cannot do that and as a newbie I want to know if it is a bug or by design. Thanks.

---

### Post by Whiffle on 2008-04-07
What happens if you try it with dpkg -i ?

---

### Post by MountainX on 2008-04-07
> **Whiffle said:**
> What happens if you try it with dpkg -i ?

I'm not sure -- I don't have anything to install at the moment. Can you install with dpkg -i from an nfs share?

---

### Post by MountainX on 2008-04-09
I figured one issue out: if the NFS server uses root squash, it is not possible to install from the network share (assuming the install requires sudo, which it usually does).

However, I believe there is something more going on. Can anyone confirm for me that they are able to install a .deb package from an NFS share? Thanks.

---

### Post by fsmithred on 2008-04-09
I just did it between two debian etch machines (don't have two ubuntu installations here to try) and it worked fine, with root_squash set. 

It works if I do it as root or with sudo, using dpkg -i. Removed them ok, too.

---

### Post by MountainX on 2008-04-09
Thank you! At least now I know this can be fixed.

---

