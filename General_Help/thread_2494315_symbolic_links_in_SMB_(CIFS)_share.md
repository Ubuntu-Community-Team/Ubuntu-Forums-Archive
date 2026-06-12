---
title: "symbolic links in SMB (CIFS) share"
date: 2024-01-12
forum: General Help
---

### Post by nasgul on 2024-01-12
I have a Proxmox 8.1.3 server running a TrueNAS Core 13.0-U6.1 VM and an Ubuntu 22.04.3 LTS VM. I have a SMB (CIFS) share on the TrueNAS VM. I have mounted the SMB share to my Ubuntu VM in the **/etc/fstab** file. I created a UrBackup server Docker instance on the Ubuntu VM with the intention of using the SMB share as the backup destination. When I run the UrBackup web UI, I get this error in the GUI:
> (err_cannot_create_symbolic_links). Operation not supported (code: 95)

UrBackup cannot create symbolic links on the backup storage. Your backup storage must support symbolic links in order for UrBackup to work correctly. The UrBackup Server must run as administrative user on Windows (If not you get error code 1314). Note: As of 2016-05-07 samba (which is used by many Linux based NAS operating systems for Windows file sharing) has not implemented the necessary functionality to support symbolic link creation from Windows (With this you get error code 4390).

this is what my **/etc/fstab** looks like:
```
//ip_address/system_backups/ /mnt/truenas/urbackup/ cifs credentials=/home/myusername/.urbackupcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777  0       0
```


Is there a way to resolve this issue?

---

### Post by SeijiSensei on 2024-01-12
Not if you're using CIFS. Any chance you can use NFS instead?

---

### Post by nasgul on 2024-01-12
> **SeijiSensei said:**
> Not if you're using CIFS. Any chance you can use NFS instead?

I created a TrueNAS NFS dataset to share **/mnt/Volume1/urbackup** and I setup the [NFS share]("https://www.awesomescreenshot.com/image/45360731?key=1c9ea027e597bc035d6cb3e93ef6be33").


This is the TrueNAS [permissions ]("https://www.awesomescreenshot.com/image/45360309?key=43f0c07606ad97acc0eace6d68e3b587")of the /mnt/Volume1/urbackup dataset.

[IMG]https://www.awesomescreenshot.com/image/45360309?key=43f0c07606ad97acc0eace6d68e3b587[/IMG]
[IMG]https://www.awesomescreenshot.com/image/45360309?key=43f0c07606ad97acc0eace6d68e3b587[/IMG]
I mounted the NFS share on the Ubuntu etc/fstab file:
```
truenas_ip_address:/mnt/Volume1/urbackup /mnt/truenas/nfs/urbackup nfs auto,nofail,noatime,nolock,tcp,actimeo=1800,_netdev 0 0
```

This is the **df -h **result:
> truenas_ip_address:/mnt/Volume1/urbackup 2.3T 128K 2.3T 1% /mnt/truenas/nfs/urbackup

However, when I run the urbackup docker container on the Ubuntu VM, it can't join a network which means there's no web UI for me to access. I suspect this is permissions issue? What am I doing wrong?

---

### Post by SeijiSensei on 2024-01-12
Using Linux as the server and the client, I export directories with the "no_root_squash" option, e.g.,
```

$ more /etc/exports
/home           192.168.100.0/24(rw,async,no_root_squash,insecure,no_subtree_check,fsid=0)
[etc.]

```
The "fsid=0" parameter is required since I'm using NFS4. 

I then create a mount directory with root ownership and make sure /etc/passwd and /etc/group match their counterparts on the server for ordinary users. For instance, the user associated with uid 1000 should be the same on both systems. Then if I mount remote:/home as the root user, the permissions will be the same for ordinary users with matching uids.

no_root_squash has security issues if you have multiple users. I don't.

---

### Post by nasgul on 2024-01-12
My NFS share was done through the TrueNAS GUI. I'm using TrueNAS Core which is based on FreeBSD. I don't know if there's a config file such /etc/exports to add additional parameters like "fsid=0" or "no_root_squash" like you would when using a Linux machine as a NFS server. As far as I know, the available sharing permissions are those you see in the NFS share screenshot in my previous post.

---

### Post by SeijiSensei on 2024-01-12
Any other options? SSHFS?

---

### Post by nasgul on 2024-01-12
> **SeijiSensei said:**
> Any other options? SSHFS?

These are the [sharing options]("http://tinyurl.com/yljjvjr9") in TrueNAS

---

### Post by Morbius1 on 2024-01-13
Have you tried **[COLOR="#B22222"]mfsymlinks[/COLOR]** option yet?

> //ip_address/system_backups/ /mnt/truenas/urbackup/ cifs credentials=/home/myusername/.urbackupcredentials,iocharset=utf8,gid=1000,uid=1000,file_mode=0777,dir_mode=0777**[COLOR="#B22222"],mfsymlinks[/COLOR]**  0       0

---

### Post by coffeecat on 2024-07-08
Closing this thread now, because it has become a magnet for spammers (posts removed).

---

