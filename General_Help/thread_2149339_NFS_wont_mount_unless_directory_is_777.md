---
title: "NFS wont mount unless directory is 777"
date: 2013-05-28
forum: General Help
---

### Post by lledurt on 2013-05-28
O.K. I had a hard drive fail and I am setting up a new NFS server.  My old one was 10.04 and now I am at 13.04.  My clients are 10.04 and I will upgrade them when I get this worked out.

Bottom line is everything was working before.  I am using the same hosts.deny, hosts.allow and exports files, and I was getting a message "mount.nfs: access denied by server while mounting ......."   I found when I made the directory 777 on the server it worked great.

After it is mounted I can go back to 770 and it still works.  I am guessing it is an id match problem.  I have all the UID's matching in the group and passwd file.

I have also tried doing the following as directed by [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

    In /etc/default/nfs-kernel-server we set:

    NEED_SVCGSSD=no # no is default

 /etc/default/nfs-common to get UID/GID mappings from names:

    NEED_IDMAPD=yes # only needed for Ubuntu 11.10 and earlier

 /etc/idmapd.conf file to have the same contents with the correct domain names. Furthermore, this file should have the following lines in the Mapping section:

    [Mapping]

    Nobody-User = nobody
    Nobody-Group = nogroup

I also tried adding
pj=pj
parents=parents

as pj:parents is the ownership of the directory on the server.

No Dice

Any Suggestions?


Thanks
P.J.

---

### Post by zt14427 on 2013-05-28
What is wrong with having a 777 on your mounted directory.  Since you can mount NFS as read-only or read-write, you can manage rwx permissions via NFS config so that the NFS is read-only (I assume that is what you want) while still having a technically 777 system directory.

---

