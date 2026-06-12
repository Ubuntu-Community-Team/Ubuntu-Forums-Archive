---
title: "NFS server -&gt; Permission denied"
date: 2017-12-06
forum: General Help
---

### Post by turtles on 2017-12-06
Greetings all! 
I am testing out using NFS for network attached storage.
I have been reading some [guides here  ]("http://http://nfs.sourceforge.net/nfs-howto/ar01s03.html#intro_server_setup") and[ here]("http://https://help.ubuntu.com/community/NFSv4Howto") and of course ```
man exports
```.
I seem to have everything working, however I get permission denied on the client when attempting to write a file
The mount is successful:
```
mount 192.168.0.2:/srv/nfs4/homes/ /mnt/nfs/
```
Reading files on the client from the server works.

On the server I have a simple test /etc/exports ```
/srv/nfs4/homes  192.168.0.1/255.255.255.0(rw,no_subtree_check)
```
I also tried it with sec=sys like so:
```
/srv/nfs4/homes  192.168.0.1/255.255.255.0(rw,no_subtree_check,sec=sys)
```

I have nothing in /etc/hosts.deny or /etc/hosts.allow

The findmnt command gives me:
on the server:

```
&#9500;&#9472;/srv                                /dev/sdb1  ext4       rw,relatime,errors=remount-ro,data=ordered
&#9500;&#9472;/export/users                       /dev/sdb1[/nfs4/homes]
```
If I try the the sec=sys mount option on the server I get:
```
EXT4-fs (sdb1): Unrecognized mount option "sec=sys" or missing value
```

The relevant  fstab on the server is:
```
/dev/sdb1       /srv    ext4  errors=remount-ro 0
/srv/nfs4/homes/ /export/users   none    bind  0  0

```
on the client:
I run
```
mount -o rw -t nfs -o sec=sys 192.168.0.2:/srv/nfs4/homes/ /mnt/nfs/
```
```
findmnt /mnt/nfs/
TARGET   SOURCE                      FSTYPE OPTIONS                                                                                                                                                               
/mnt/nfs 192.168.0.2:/srv/nfs4/homes nfs4   rw,relatime,vers=4.0,rsize=1048576,wsize=1048576,namlen=255,hard,proto=tcp,timeo=600,retrans=2,sec=sys,clientaddr=192.168.0.4,local_lock=none,addr=192.168.0.2
```

I am working as the root user on both machines.
Any advice ?
Thanks in advance

---

### Post by Kirk Schnable on 2017-12-07
If you wish to act as the root user on the NFS client, you will possibly want this option in your export options:
no_root_squash

Without it, root will become "nobody" and thus have no permissions over files owned by anybody besides "nobody".

---

### Post by turtles on 2017-12-10
> **Kirk Schnable said:**
> If you wish to act as the root user on the NFS client, you will possibly want this option in your export options:
no_root_squash

Without it, root will become "nobody" and thus have no permissions over files owned by anybody besides "nobody".

Greetings thank you for the reply. That's fine for the nobody its just for a backup program run as root on the client.  The root user on the client needs to store encrypted backups on the server. However I cant even connect as a non root user from the client.
same error.
Thanks in advance.

---

### Post by Kirk Schnable on 2017-12-14
Check your file permissions if you're mounting as a non-root user.   Especially who has ownership over the files.  If you aren't sure what the file owner should be, try making a 777 folder and creating a file in that folder over NFS, then see who owns it.

---

### Post by turtles on 2017-12-18
> **Kirk Schnable said:**
> Check your file permissions if you're mounting as a non-root user.   Especially who has ownership over the files.  If you aren't sure what the file owner should be, try making a 777 folder and creating a file in that folder over NFS, then see who owns it.

Greetings on the server I did a:
chmod 777 /export/users

and I can write to the drive from the client.
Thanks for your help!

So my goal of a drive on the network is accomplished.
Given that I would like this thing to function like a store bought NAS some questions about nfs4 and my current setup remain:

my current /etc/exports on the server contains:
```
/srv/nfs4/homes  192.168.0.1/255.255.255.0(rw,no_subtree_check,sec=sys)
```

So that will allow anyone on the 192.168.0.1 subnet to drop files on the drive.
and anyone on that subnet can retrieve and or delete the files.
If anyone wants to store a private file they will need to encrypt it first.


1) What is the bind mount on the server side for?
in my server side fstab I have ```
/dev/sdb1       /srv    ext4  errors=remount-ro 0
/srv/nfs4/homes/ /export/users   none    bind,sec=sys  0  0

```

perhaps I can just mount /export/users directly?


and 
2) What would be a better security set up for a simple home office NAS? 
I read about [kerberos]("https://help.ubuntu.com/lts/serverguide/kerberos.html")
and am hoping there is a simpler option.

Thanks in advance.

EDIT: Actually users permissions are preserved on the drive

---

