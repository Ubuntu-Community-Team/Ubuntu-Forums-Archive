---
title: "Browsing samba shares in text mode."
date: 2004-11-07
forum: General Help
---

### Post by tvlad on 2004-11-07
The only way i know how to do that in text mode is by using smbclient -L localhost, then smbclient -L HOST, then smbmount or mount -t smbfs.

Before i could do that in Ubuntu, i had to install Samba, in order to start smbd, though i saw that Nautilus showed me all the samba shares even before i had installed Samba, so i'm guessing there should be another way as well.

---

