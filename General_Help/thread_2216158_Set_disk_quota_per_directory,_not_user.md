---
title: "Set disk quota per directory, not user?"
date: 2014-04-10
forum: General Help
---

### Post by dsmithhfx on 2014-04-10
Hi,

I'm running 10.04 LTS server as a staging (web) server, with /var/www accessible over our lan via afp. The server has limited storage, and occasionally users put fairly large files on it for download. I would like to set a limit/disk quota on this directory, as a precaution against user(s) completely filling the disk, with unpleasant consequences to the server. 

Can anyone suggest a method for doing so, apart from the relatively cumbersome method of creating a disk image for it?

Thanks!

---

### Post by Little_Nooby on 2014-04-10
My solution is maybe heavy but it should work : Create partition with the right size. Mount the partition to the folder.
Now, thinking of that, I don't know what it would do if the user try to over fill it. Yeah, I don't like it either.

Mmmmh, how do I delete my post?

---

