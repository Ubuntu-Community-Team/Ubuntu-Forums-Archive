---
title: "Can't get printer to work"
date: 2006-12-07
forum: General Help
---

### Post by jumbojs on 2006-12-07
I'm trying to connect to a Canon i560 printer on a Windows XP machine. I've checked all the sharing connections and I can connect the printer to other machines on the network, but not my Linux machine. I can ping the windows machine and it works. I've tried alot. I keep getting this message. 'Printing: Unable to connect to CIFS host, will retry in 60 seconds...' Any help would be appreciated.

---

### Post by dcstar on 2006-12-07
> **jumbojs said:**
> I'm trying to connect to a Canon i560 printer on a Windows XP machine. I've checked all the sharing connections and I can connect the printer to other machines on the network, but not my Linux machine. I can ping the windows machine and it works. I've tried alot. I keep getting this message. 'Printing: Unable to connect to CIFS host, will retry in 60 seconds...' Any help would be appreciated.

If this is on a corporate network, chances are you do not have permissions unless the Linux box is authenticated to the Windows domain.

You may have to manually check the permissions on the printer share.

---

