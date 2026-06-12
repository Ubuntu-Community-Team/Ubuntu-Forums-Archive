---
title: "umask ignored on NFS mounts"
date: 2018-07-02
forum: General Help
---

### Post by Mr. Shannon on 2018-07-02
I have a rather interesting problem. Starting about 3 AM last night all files/directories created on my NFS mounts completely ignore the umask. I have a domain-wide umask (for all users except root) of 0002 set but all files and directories created on NFS mounts get 666 or 777 as their permissions. This does not affect files and directories created locally on the client, or on the NFS share when created locally on the NFS share. I can fix the permissions after creation from the client with chmod so it's not a larger permissions issue, the umask is just being ignored.

My fstab entries look like:
```
fileserver.san:/srv/projects        /srv/projects    nfs4    defaults,timeo=14,_netdev,noacl    0 0
```
And my /etc/fstab entires look like:
```
/srv/projects    128.xxx.xxx.2(rw,no_subtree_check,crossmnt)  128.xxx.xxx.3(rw,no_subtree_check,crossmnt)
```
I am running kernel 4.15.0-24-generic, fully updated Ubuntu 18.04 on the server and all clients.

**EDIT:** I can confirm that forcing NFSv3 fixes the problem so it is limited to NFSv4. Further testing, shows it only occurs on NFSv4.2, NFSv4.1 and NFSv4.0 seem to be unaffected.

**EDIT: **I am fairly certain now that this is a bug and have file the following bug report: [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1779736](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1779736)

---

