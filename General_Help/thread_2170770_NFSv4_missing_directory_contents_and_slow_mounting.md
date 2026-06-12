---
title: "NFSv4 missing directory contents and slow mounting"
date: 2013-08-27
forum: General Help
---

### Post by Untarnished_Truth on 2013-08-27
I am setting up a group of PCs to use NFS.  The NFS server is running Ubuntu 12.04 LTS, one client is running Ubuntu 13.04, and another client is running OpenSUSE 12.3.  I followed the instructions in [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto), simple NFSv4 without Kerberos for now.

I ran into problems for both clients.
(1) On my Ubuntu client, executing ```
mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/users /home/users
``` mounts my exported directory, as shown by "df -h". However, if I cd into the mounted directory in the client, the contents (files and subdirectories) are all missing. Why are the contents missing?
(2) Executing "mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/users /home/users" on my openSUSE client mounted everything inside my exported directory perfectly, unlike (1) above. However, the mounting process takes a while (15 seconds).  If I run "rpc.gssd -f -v" simultaneously on another terminal, the mounting process takes place instantaneously, with the contents of exported directory are all present, as they should be. Is there a way to achieve this end result without having to run rpc.gssd?

---

