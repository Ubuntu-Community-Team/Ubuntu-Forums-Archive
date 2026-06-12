---
title: "NFS Mount uid=nobody"
date: 2008-05-21
forum: General Help
---

### Post by kbailey33 on 2008-05-21
I am having a problem with an NFS Mount.  We have two ubuntu servers, one shared home directory.  We are using samba, winbind and krb with active directory authentication.  On the server that we have the nfs mounted (home directories) the users get a uid of nobody instead of their uid and domain users.  I believe this can be fixed either via my export or in the mount command but I am not sure what to change.

My /etc/export on server 1 reads
/home *(rw,sync,no_root_squash)

the fstab on server 2 reads

server1:/home/domain /nfshome nfs rsize=8192,wsize=8192,timeo=14,intr

Any help would be appreciated.

---

