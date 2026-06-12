---
title: "High RAM on Ubuntu SMB Server"
date: 2024-11-09
forum: General Help
---

### Post by Steven_Wittwer on 2024-11-09
I have a Proxmox VM using Ubuntu 24.04 Server.  It's only job is to run Samba shares for our network.  Active Director access is used as well as ACLs to define permissions.

All is well after a reboot until I transfer a large(ish) file.  As soon as I transfer a large file over the network, the used RAM goes to 93-95% and never goes down unless I reboot.

htop doesn't show anything using high RAM, but it only shows 237 MB free of 8 GB. [See Attachment]

Is this something I should be concerned about?

---

### Post by andreas292 on 2024-11-09
think here is an misunderstand. Your system use only 226MB (+some swap) of 8GB RAM. Samba don´t need so much ram.

---

### Post by Steven_Wittwer on 2024-11-09
> **andreas292 said:**
> think here is an misunderstand. Your system use only 226MB (+some swap) of 8GB RAM. Samba don´t need so much ram.
ah, ok, that makes sense.  It must be something in Proxmox then that is reporting extra RAM in use.  Proxmox shows 94% used, but it does the same thing on a Windows guest, but task manager in Windows clearly shows that is not the case.

Thanks for the info.

---

