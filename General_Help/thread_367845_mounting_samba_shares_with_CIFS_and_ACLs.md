---
title: "mounting samba shares with CIFS and ACLs"
date: 2007-02-22
forum: General Help
---

### Post by mike4ubuntu on 2007-02-22
I can't get samba shares mounted in /etc/fstab as type CIFS to work with ACLs.  The ACLs work ok locally on the machine where the directory is shared.  The commands setfacl and getfacl work ok locally with groups and users defined locally.  However, on the remote machine that mounts the shares, the ACLs don't appear to be there.  Even after creating the same users and groups on the remote client.  Is there anything I have to do with samba configuration on the server or client to get it to recognize the ACLs?

---

