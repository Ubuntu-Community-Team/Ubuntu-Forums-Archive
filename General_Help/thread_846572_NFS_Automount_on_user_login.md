---
title: "NFS Automount on user login"
date: 2008-07-01
forum: General Help
---

### Post by mattofak on 2008-07-01
Hey All;

I was wondering if there is a solution for automounting NFS shares on user logon. The reason I can't use /etc/fstab is because different users will have different shares mounted, and they will need to be able to login using their network domain credentials. I was hoping there might be some sort of '.nfsmount' file I could put in their /home/* directory for this automount behaviour.

They're logging onto the workstations with domain creds, so they're cached in PAM for use. The closest I can come to for this seems to be pammount, but thats also, so far as I can tell only for SMB shares.

Thanks for any ideas;
Matthew Walker

---

### Post by RealPSL on 2008-07-04
What you are looking for is autofs. Assuming that the export of the NFS is already complete review the link below starting at the Setting up clients for nfs and autofs

[https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto]("https://help.ubuntu.com/community/FedoraDirectoryServerClientHowto")

---

### Post by txcrackers on 2008-07-04
I think what you're looking for is FUSE (Filesystem in Userspace). Here's the Wikipedia article, which is a good place to start:

[http://en.wikipedia.org/wiki/Filesystem_in_Userspace](http://en.wikipedia.org/wiki/Filesystem_in_Userspace)

---

