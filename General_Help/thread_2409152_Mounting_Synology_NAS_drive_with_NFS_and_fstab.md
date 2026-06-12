---
title: "Mounting Synology NAS drive with NFS and fstab"
date: 2018-12-28
forum: General Help
---

### Post by Adam_Jacobs on 2018-12-28
I have a Synology NAS drive which I had previously mounted via fstab with CIFS. This worked just fine until I upgraded to 18.04, and now I have the problem described in [this thread]("https://ubuntuforums.org/showthread.php?t=2409042").

It occurred to me that maybe things would work better if I mounted with NFS instead of CIFS. So I followed the instructions in [this article]("https://www.synology.com/en-uk/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS").

That sort of worked. I can mount my NAS drive manually using the mount command, and once I've done so, the problems described in the other thread appear to be solved. However, what I would really like to do is to mount the NAS drive in fstab so that it's permanently mounted. But that doesn't seem to work. Here is the relevant line from my fstab:

```
synology.local:volume1/htpc/    media/synology    nfs    auto,_netdev    0    0
```

That doesn't mount it at startup, and if I try to mount it via sudo mount -a, I get the following error message:

mount.nfs: access denied by server while mounting synology.local:volume1/htpc

Clearly the server is happy enough to let me in, because I can do it manually using the mount command. I'm assuming that there must be something wrong with my fstab syntax, but despite extensive googling, I have no idea what.

Any ideas?

---

### Post by CatKiller on 2018-12-28
In case it helps, my fstab line to do similar, which works, is ```
diskstation:/volume1/downloads  /mnt/nfs/downloads      nfs     auto,noatime,nfsvers=4       0       0
```
The *diskstation* in that line is because I've got that as an alias in /etc/hosts, otherwise I suspect that I'd need to use the IP address there. You've also missed the leading / from the path of your mount point. I've also got "map all users to admin" set on the Synology share: it's possible that your normal user can do things that root can't with the way that your share is set up.

---

### Post by Adam_Jacobs on 2018-12-29
Thanks! I'm not entirely sure I understand why, but adding nfsvers=4 to the options did the trick, at least it did when I also ticked the box on the Synology device to enable NFS4.1, which was off by default. It all works OK now :)

Not sure what happened to my leading slash in the code above: it was there in my fstab, but somehow seems to have jumped over to be a trailing slash on the NAS path (which wasn't there in my fstab) when I paste the code in here. But no matter, the slashes were all in the right place in my fstab.

---

