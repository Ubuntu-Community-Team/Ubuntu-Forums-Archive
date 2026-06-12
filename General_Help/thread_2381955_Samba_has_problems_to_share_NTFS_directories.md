---
title: "Samba has problems to share NTFS directories"
date: 2018-01-07
forum: General Help
---

### Post by mert.srmog on 2018-01-07
Hi,

I can share on my local network via Nautilus (right click any folder --> Properties --> Local Network Share). I can access the files from any other machines without any issue.

But if I share a folder which is under NTFS partition, I can see the folder name on public network but I can not access inside of it.  It gives this error:

"Failed to mount Windows share: Permission denied"

1- The folder which I'm sharing has all permissions to everyone:
ls -ld /mounted/ntfsPartition/myFolder
drwxrwxrwx
That mean everyone has access for these files. Samba can access and samba can share it with anoyone.

2- I mount the ntfspartition with Nautilus file manager.

3- I have did all updates on Ubuntu 16.04. This is not important because I have this problem since many years.

4- I have no my own configuration on system. Everything is default. I did not touch anything yet after installed Ubuntu.

5- I restart the samba service and my OS many times. 

Can you please tell me how can I solve this problem?

Thank you

---

### Post by TheFu on 2018-01-07
Welcome to the forums.

This post is about what I would recommend, stuff that works.

Sharing NTFS from Linux will always have issues.  Linux sharing expects Unix/POSIX permissions.  NTFS support for those is a hack and limited.

So, the first advice is switch from NTFS to any Linux file system.  EXT4 would be the default choice, but there are others if you have specialized needs.

So, assuming you switch to a Linux-based file system (not NTFS), then ... 

For internet-based file access, use sftp:// - all Linux file browsers should support that URL. Install openssh-server and you get sftp file services for free. You also get sshfs, rsync-over-ssh, and lots of other capabilities. These are all  tied to the ssh port, ssh authentication and ssh-keys (which are both more secure and more convenient).

For LAN file access between Unix systems, use NFS. It is a no-brainer.  NFS makes LAN storage seem like local storage. Ownership, groups, permissions are all native.

For LAN file access from a Windows client, you can use sftp/scp with WinSCP.  Or, if you must, use samba.  Samba is a weak choice and if you use Windows, the chance that samba connected storage will be malware encrypted isn't zero.

I've never used any GUI to deal with storage sharing or mounts.  If those GUIs are typical for Unix systems, they provide 20% of the features.  When doing odd things, like sharing NTFS file systems, that isn't sufficient.

IMHO.  YMMV.

If you are stuck with NTFS, expect issues on Linux.  There are times when NTFS is the best choice, but those are usually when you have to physically connect the storage to a Windows machine.  If you don't physically need to connect this storage to Windows, switch to a Unix file system. All this stuff will work better.

---

