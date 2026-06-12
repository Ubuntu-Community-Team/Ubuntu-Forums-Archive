---
title: "moving /home partition with correct permission structure"
date: 2007-02-01
forum: General Help
---

### Post by Odyssey1942 on 2007-02-01
OK, now have my computer booting from either 5.04 (old hdd) or 6.10 (new hdd). I want to move my /home from the old 5.04 to the new 6.10, repartition the 5.04 and install 6.10 onto that old hdd as well and move the /home back to the old hdd (now also 6.10) on a separate partition.

There are a quantity of business files from the last few years (all created under Windows) but copied to the /home directory of the 5.04. So far so good.

I wanted to create a group of office associates who would be ordinary users (not administrators) with read, write (and execute) rights to all these files. I had previously tried unsuccessfully to create this group under me (i.e., in my /home), but am recently advised that the files (let's call them Office) need to be moved from my /home to the top (not sure what that means, but maybe as /office under root?) and a group formed with the desired permissions to access /Office.

I expect that both of the above objectives (copying /home and creating a group to access Office) are best done together, but I really cannot get my head round the way to do it.

Can someone guide me through this (as much as possible in a step by step description, thanks)?

---

### Post by Odyssey1942 on 2007-02-04
No one?

---

### Post by elsaturnino on 2007-09-25
Sorry to dig this out of the garbage bin (it came up as being related to a post I wanted to make) but what you can do is create a directory under home, let's say "/home/office." Change the owner to yourself (chown) and the group (chgrp) to the group name you want and just set the permissions for this directory so that the owner and group have full rwx privileges.

---

