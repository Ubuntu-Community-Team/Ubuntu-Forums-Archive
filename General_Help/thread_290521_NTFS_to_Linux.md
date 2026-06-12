---
title: "NTFS to Linux"
date: 2006-11-01
forum: General Help
---

### Post by Moeru on 2006-11-01
I'm planning on moving my large file server over to Ubuntu. My only concern is what the possible problems are when writing from Windows to the file server. I've got multiple PCs in the house and 2 of them have to stay Windows (not my PCs). Is this going to be a problem or has NTFS read\write gotten far enough where this won't be a problem?

---

### Post by Ramses de Norre on 2006-11-01
When you write from windows over the network to your file server the actual writing will be done by the OS of the file server (and vice versa) so it doesn't matter which OS/filesystem you use.
And there are possibilities enough to network between ubuntu and windows.

---

### Post by dbott67 on 2006-11-01
Partition the storage volume on the server to be FAT and you should be okay.  I'm assuming that you're setting up an Ubuntu server and will have Windows PCs and some Linux machines.  The native file system on the client will have no bearing on the ability to read/write files to the network.  So, it doesn't matter if the XP machines use NTFS or FAT32 for the local file system --- they will still be able to write to the file server's FAT partition.

Setup Samba on the Ubuntu server, as well as samba, smbfs & smbclient on any Ubuntu clients PCs.

-Dave

---

