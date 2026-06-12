---
title: "Unexpected result for chown command"
date: 2024-10-28
forum: General Help
---

### Post by makem2 on 2024-10-28
```
makem@makem-22:/media$ ls -latotal 16
drwxr-xr-x   6 root  root  4096 Oct 28 16:33 .
drwxr-xr-x  23 root  root  4096 Oct 27 16:22 ..
drwxr-xr-x   4 makem makem 4096 Oct 27 21:29 data
drwxr-x---+  2 root  root  4096 Oct 28 07:21 makem
drwxrwxrwx   1    99 users   22 Oct 11 21:53 my-domain
drwxrwxrwx   1    99 users   16 Sep 27 19:30 nas-data
makem@makem-22:/media$
```

The mount point nas-data was owned by root:root and I wanted to change it to makem:makem

I used the command sudo chown -R makem:makem nas-data as I had done when I changed data above. However this time it changed to drwxrwxrwx   1    99 users   16 Sep 27 19:30 nas-data as in the output above. Not only that but the my-domain mount point also had a similar change.

Why did that happen, what are the consequences and how to I correct it please.

I think this occurred because of the -R which I now believe should not be used for mount points for mount points. The 99 users may be the number of files in one folder in the nas-data mount

---

### Post by TheFu on 2024-10-29
This seems like a NAS-specific issue, since normal NFS wouldn't allow root from a client to change any owners by default.  What NAS model and software is being used?
Also, which file systems are used on the remote storage?

Ownership of mount points requires the remote storage to be mounted and the file system to be NFS or 9p or something non-samba/CIFS to work.

The /media/makem directory is using ACLs so we can't trust the output above.

There are just lots of unexpected things shown above.  Can you show the output from 
```
df -Th |grep media
```
and the fstab entries that provide the mounts would be useful as well.

---

### Post by makem2 on 2024-10-30
> **TheFu said:**
> This seems like a NAS-specific issue, since normal NFS wouldn't allow root from a client to change any owners by default.  What NAS model and software is being used?
Also, which file systems are used on the remote storage?

Ownership of mount points requires the remote storage to be mounted and the file system to be NFS or 9p or something non-samba/CIFS to work.

The /media/makem directory is using ACLs so we can't trust the output above.

There are just lots of unexpected things shown above.  Can you show the output from 
```
df -Th |grep media
```
and the fstab entries that provide the mounts would be useful as well.

The output I received appears normal and is acting normally in my circumstances of:

Extract from /etc/fstab:

# my-domain auto mount
192.168.1.249:/mnt/user/my-domain /media/my-domain nfs x-systemd.automount 0 0


# data folder in nas auto mount
192.168.1.249:/mnt/user/data /media/nas-data nfs x-systemd.automount 0 0

```

makem@makem-22:~$ df -Th |grep media
/dev/nvme2n1p1                    ext4      1.8T  440G  1.3T  26% /media/data
192.168.1.249:/mnt/user/my-domain nfs4      7.3T  458G  6.9T   7% /media/my-domain
192.168.1.249:/mnt/user/data      nfs4      8.2T  504G  7.7T   7% /media/nas-data
/dev/sda1                         vfat       30G  518M   30G   2% /media/makem/disk
makem@makem-22:~$

```

It was my inexperience and lack of knowledge, never having seen such a result that caused my post.

Thank you for your input.

---

### Post by TheFu on 2024-10-30
```
makem@makem-22:/media$ ls -al 
drwxrwxrwx   1    **99** **users**   16 Sep 27 19:30 nas-data
```

Having 777 permissions is pretty lazy, but ... whatever. Poor security is your choice.

So, how did the owner:group get set to 99:users?  Which model NAS is this?  Or is it an ubuntu server?  If you want a client root/sudo to be able to chown, you'll need to change the default NFS option in the exports from the NFS-server to allow that.  This is a bad security choice.  Otherwise log into the NFS server and set the owner/group uid/gid to the values you want  using sudo on that system.  The numbers you would use are on the client-side and can be seen using the 'id makem' command.  Typically, the first created userid has a uid of 1000 and gid of 1000.  These numbers are coincidental, not fixed and the fact they are the same is meaningless.  

If you want to allow other users read-write access to the same NAS storage, then you'll need for the users to be in the same group on all client systems.  Having centralized user management make this stuff easier, but it is a bit of a hassle.

---

