---
title: "deluge problems"
date: 2007-10-06
forum: General Help
---

### Post by driectly3d on 2007-10-06
im trying to download a torrent, but for somereason it keeps pausing and unpausing every three seconds in deluge, any ideas on what this might be?

---

### Post by dreaswar on 2007-12-26
hi...
i hve the same problems with deluge. 

it ran well initially for about a week and now it is exibitng this behavior. 

i run Ubuntu 7 .10. Its a fresh install. 

I have tried completely removing it and reinstalling it form synaptic but that dosent work.. 

Any ideas.....

Of course you can install Utorrent through Wine and also there is Ktorrent. 

Anything to get Deluge working ??

Thnks..

---

### Post by dreaswar on 2007-12-26
HI.. 

Problem solved. 

Reinstalled the latest  version of Deluge from the website after deleting the deluge folder under /.config

Found out that the permission on my NTFS drive had changed . ntfs read write utility (ntfs-3g) bundled with ubuntu had mysteriously uninstalled. I reinstalled that.

I had messed up my fuse-utils, lib-dev and other things yesterday while trying out Acetone iso. Reinstalled all things required for NTFS support by searching "NTFS" under synaptic.

hope that helps.

---

