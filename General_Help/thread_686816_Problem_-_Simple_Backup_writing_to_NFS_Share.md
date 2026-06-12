---
title: "Problem - Simple Backup writing to NFS Share"
date: 2008-02-03
forum: General Help
---

### Post by GerryGG on 2008-02-03
I am trying to use Simple Backup to make a backup and write it directly to another Ubuntu computer on my local network. I have NFS set up, and have successfully mounted a share from the other computer onto my computer with read and write permissions. (That is, I am able to create files on this share from my computer and they show up on the other computer. So, the NFS seems to be working fine.) The problem is that when I run Simple Backup and tell it to use this mount point as the destination, it tells me I don't have permission to write there. I read in other threads that for Simple Backup to work properly with NFS, the destination (mount point) has to be created by root. So, I created a folder as root, and confirmed that root was the owner (with read and write permissions). I then mounted the share, and the ownership of the mount point changed to my user name. So, maybe that is why Simple Backup said it couldn't write to the folder/mounted NFS as it was owned by my user name and not by root. As soon as I unmount the share, the folder ownership goes back to root. So, if anyone could answer any of these questions, much appreciated:

1. Can you confirm that it is possible to write to an NFS mounted share with Simple Backup?
2. If so, does this share/mount point have to be owned by root?
3. If so, how do I get a share/mount point owned by root when the process of mounting the share seems to change the ownership to my username? (Simply trying to change the ownership back to root, while the share is mounted, doesn't work.)

Many thanks for any light you can shed on this. (I'm using Ubuntu 7.10, in case it matters.)

---

### Post by Zill on 2008-02-05
GerryGG:  I successfully use SBackup and NFS as you have described so answers as follows:
1)  Yes
2)  Yes
3a)  Ensure both the NFS client destination directory and the unmounted NFS server mount directory (/mnt/xxx) are owned by root with rwx permissions.
3b)  The NFS server /etc/exports file should include the "no_root_squash" option.  eg:
/destinationpc       192.168.0.3(sync,no_root_squash,rw)
3c)  Include the NFS mount point in the client /etc/fstab file and then reboot.  This will ensure that this is mounted by root at bootup.
3d)  Run SBackup with /mnt/xxx as the destination directory.

I have assumed that hosts, hosts.allow and hosts.deny are all set up correctly on both PCs.  Hopefully this will now work for you - if not then please advise ;-)

---

### Post by GerryGG on 2008-02-05
Hi Zill,

Many thanks for your tips. I'll work through them, and hopefully get things sorted out.

---

### Post by GerryGG on 2008-02-06
Zill, Thanks again. I got it to work. I think the no_root_squash option was the key, as the mount point on my computer remained owned by root, even after mounting the share, whereas before the mounting process would change the ownership back to my user account, and Simple Backup would complain that it can't write to the selected directory (presumably because it wasn't owned by root. Now, Simple Backup accepts the directory, and the backup is occurring as I type this and is automatically going onto the other computer on the network, as I had wanted.

I haven't yet tried to automate this through the /etc/fstab. But, at least I got it going "manually".

You mentioned that host, hosts.allow and hosts.deny should be set up on both computers as well. I haven't checked into this yet. (I don't know whether they are set up or not.)

---

### Post by Zill on 2008-02-07
GerryGG:  Glad you got it working :-)

/etc/hosts should have both client and server ip addresses on both PCs.  AIUI, hosts.deny and hosts.allow provide more security for things like NFS.  However, if your LAN is behind a router then security shouldn't be a problem(!!!)

My /etc/hosts.deny has the following line:
```
ALL: ALL
```
My /etc/hosts.allow has the following line:
```
ALL: 127.0.0.1 192.168.0.
```

Although you *can* manually stop and start relevant services such as portmap, nfs-kernel-server and nfs-common, after tinkering with NFS files I have found that rebooting avoids a lot of problems.  Not the Linux way, I know, but it works for me :-)

---

