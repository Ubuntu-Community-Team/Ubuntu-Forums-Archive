---
title: "network share, samba alternative"
date: 2014-02-28
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2014-02-28
i know samba is for windows networks, i don't have any window machines on the network so is there a linux specific one?

---

### Post by Morbius1 on 2014-02-28
Your premise is incorrect. Apple for instance has shifted from using it's own afp file sharing protocol to SMB as the default. 

*Side note: In fact it was to be Samba itself but there seems to have been some kind of licensing dispute and Apple told Samba to procreate itself so they wrote their own. Mistake for Samba. Any interaction between Apple and anything Linux related benefits Linux - think CUPS.* * It can work in 2 host discovery modes - one using Microsofts protocols and one using it's own called Bonjour ( in Linux Bonjour is called Avahi ).*

But I digress. [COLOR=#000000]The only socially acceptable answer to your question in a Linux forum is NFS.[/COLOR] If you change the title of your thread to "All linux network, samba alternative" you will have to beat away the NFS'ers away with a stick ;)

---

### Post by lukeiamyourfather on 2014-02-28
Look at NFS. You can install it with this.

```
sudo apt-get install nfs-kernel-server
```

To share a directory with read and write permissions for everybody change the directory owner to nobody.nogroup and add the line below to /etc/exports file.

```
/stuff/to/share		*(rw,async,insecure,all_squash,no_subtree_check)
```

Then restart the NFS server.

```
sudo service nfs-kernel-server restart
```

If you want to share specific stuff with specific users and enforce security you can do that with NFS too. See the manual for it. 

```
man exports
```

Also see the Ubuntu help on it.

[https://help.ubuntu.com/12.04/serverguide/network-file-system.html](https://help.ubuntu.com/12.04/serverguide/network-file-system.html)
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by pqwoerituytrueiwoq on 2014-02-28
thanks, i manged to get samba working after making the thread, i will leave that like it is for now
will try nfs next time

---

