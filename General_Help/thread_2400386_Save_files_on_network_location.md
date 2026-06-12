---
title: "Save files on network location"
date: 2018-09-05
forum: General Help
---

### Post by ckrles on 2018-09-05
Hi, I have ubuntu 16.04.
I can access my synology Nas through nautilus, but I can't get programs like telegram to save files in my Nas. The opti9n doesn't appear in the dialog box. I choose "other location" and I can only see the / partition and my windows partition (I have dual boot).

Any ideas on how to make these programs save the files in my synology? Access to the synology requires a user and a password, which I could somehow avoid by using a guest account.

Any ideas?

Thank you very much.
I have been looking for an answer but I was unable to find it.

---

### Post by SeijiSensei on 2018-09-05
The simplest solution is to mount the exported filesystem into the Linux filesystem.  If the NAS supports the NFS protocol, I'd use that.  

[https://help.ubuntu.com/lts/serverguide/network-file-system.html.en#nfs-client-configuration](https://help.ubuntu.com/lts/serverguide/network-file-system.html.en#nfs-client-configuration)

---

### Post by ckrles on 2018-09-05
> **SeijiSensei said:**
> The simplest solution is to mount the exported filesystem into the Linux filesystem.  If the NAS supports the NFS protocol, I'd use that.  

[https://help.ubuntu.com/lts/serverguide/network-file-system.html.en#nfs-client-configuration](https://help.ubuntu.com/lts/serverguide/network-file-system.html.en#nfs-client-configuration)

Thanks. I've tried it but it'a a bit confusing. I'm kind of a noob.

---

