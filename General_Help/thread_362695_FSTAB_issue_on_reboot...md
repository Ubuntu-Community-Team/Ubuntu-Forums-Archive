---
title: "FSTAB issue on reboot.."
date: 2007-02-15
forum: General Help
---

### Post by tiger.woods on 2007-02-15
I have what I think is a quick question for someone with more Linux knowledge than myself.

I've created an export in my /etc/exports file on my server that I want to mount on my client via /etc/fstab.

I think I've set up the exports correctly - 

/directorytoexport 192.168.1.1(rw,no_root_squash,async) 

and the fstab correctly on the client - 

192.168.1.2:/directorytoexport /directorytomount nfs rw, defaults 0 0

The share is identified on the client by an icon but says, "Unmounted NFS share" even after rebooting, Iwas able to ultimately mount it manually after a LONG delay but defeats the purpose of the fstab. 

Anyone have any ideas what I've done wrong and why it didn't mount in the fstab???

This is on an Ubuntu Edgy if that help.

T.I.A

TW,

---

### Post by tiger.woods on 2007-02-17
wow! no reply's on an fstab issue cmon' guy's?

---

