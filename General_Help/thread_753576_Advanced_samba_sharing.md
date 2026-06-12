---
title: "Advanced samba sharing"
date: 2008-04-12
forum: General Help
---

### Post by Tyke91 on 2008-04-12
I tried to do this a while ago, but failed miserably.

I'd like to use samba to create a long distance shared folder with more than one user. each user is likely to have his/her own password and I'd like to give some users read/write access and others just read access.

I have no clue how to accomplish this however. I can configure my computer to have the shared folder, and I can configure a static IP address for the box, but how do I make the share accessible to other users (both windows and linux) outside of my personal LAN network.

ALSO: what kind of security threat would this pose? the share is owned by my user account, but I did use sudo to configure it as "Shareable", so would an attacker be able to gain root access through this shared folder?

---

### Post by dcstar on 2008-04-12
> **Tyke91 said:**
> 
..........
ALSO: what kind of security threat would this pose? the share is owned by my user account, but I did use sudo to configure it as "Shareable", so would an attacker be able to gain root access through this shared folder?

A shared folder is just that, a folder where files reside. Nothing "runs" on the machine where the folder resides, it just allows read and/or write access to the folder.

The only "Security" issue would be to allow a user to fill up the shared folder to 100% full, and if are silly enough to have that folder in your root filesystem then that can crash your system.

---

### Post by Tyke91 on 2008-04-12
that's good :) so, any advice about accomplishing this feat?

---

