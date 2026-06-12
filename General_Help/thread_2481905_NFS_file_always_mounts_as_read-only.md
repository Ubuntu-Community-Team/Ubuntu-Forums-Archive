---
title: "NFS file always mounts as read-only"
date: 2022-12-12
forum: General Help
---

### Post by BudworthTDog on 2022-12-12
I recently built a new and updated computer and loaded Ubuntu Mate 22.04 on it. I have a QNAP NAS on my network that I am trying to connect to, well I *can* connect to it but it wont let me edit it as it constantly mounts it as read-only. I'm convinced it can't be any of the settings on the QNAP NAS because it worked fine before and I didn't change a thing on it. 

I used the same guide as my previous install to mount the NAS. Found here. 

[https://sites.google.com/site/installationubuntu/qnap/qnap-nfs-shares-on-ubuntu?pli=1](https://sites.google.com/site/installationubuntu/qnap/qnap-nfs-shares-on-ubuntu?pli=1)

I follow the directions there. It mounts it and I can access the files, but I can't create files or add files. I tried adding "-o rw" to the mount command but it still mounts it as read-only. It mounts it with root as the owner. I've tried chown of the mount point but it gives me the following error 

chown: changing ownership of 'NFSmountpoint': Read-only file system

Any ideas?

---

### Post by TheFu on 2022-12-13
a) please post the mount options as shown by the 'mount' command on the client for the NFS storage
b) 'showmount -e' from the server
c) please post the mount line in the fstab or autofs config file used.
d) please show the 'ls -la' of the  directory where you cannot write/create files from both the client and server sides.
e) please post the 'id' command output for the userid that isn't working.

'chown' shouldn't work from any client.  'root' privilege is squashed by normal NFS, so only the server with the storage can run chown or chmod.  Once the owner is corrected, then the owner can use chgrp/chmod at will.  I suspect the new install has a different uid/gid than the old one did.  The uid/gid need to map 1-for-1 between the client and server storage.

The read-only mount, if proven, is either in the mount from the client or in what the server is sharing.

I ask for the posted information **(please use 'forum code tags')**, so we have facts, not interpretations of stuff.  Also, I suspect you'll see the issue in gathering the requested info.

---

### Post by BudworthTDog on 2022-12-13
Thank you for your reply. 

A. "mount options as shown by the 'mount' command on the client for the NFS storage" I'm not sure if this is what you were referring to but I will post the mount command I am using to mount the NFS. it is as follows. (without ip address redacted) 

```
sudo mount -t nfs xxx.xxx.xxx.xxx:/Public /media/missethel/NFSmountpoint
```

B. 'showmount -e' from the server

The server in this case is a QNAP NAS. Model number TS-433. From what I had gathered it runs on Linux, but I'm not positive. I used ssh to get into the terminal of the NAS but when I ran 'showmount -e' I got an error stating "showmount: command not found"

C. mount line in the fstab or autofs config file used

I used fstab and put in the following line (without ip address redacted)

```
xxx.xxx.xxx.xxx:/Public /media/missethel/NFSmountpoint  nfs defaults,bg 0 0
```

D. please show the 'ls -la' of the  directory where you cannot write/create files from both the client and server sides.

From client:
```
total 100
drwxrwxrwx    8 root      root       4096 Dec 12 17:06  .
drwxrwx---+   5 missethel missethel  4096 Dec 13 16:07  ..
drwxrwxrwx    2 missethel users     69632 Dec 13 08:54  Movies
drwxrwxrwx    2 root      root       4096 Dec  7 16:42  @Recycle
drwxrwxrwx    5 missethel missethel  4096 Dec 12 00:20  .Trash-1000
drwxrwxrwx  306 missethel users     12288 Dec 12 14:11 'TV Shows'
drwxrwxrwx    2 missethel users      4096 Dec 13 15:52  .@upload_cache
```

Server:
```
total 8
drwxrwxrwx 2 nathankirwin everyone       4096 2022-12-07 17:12 ./
drwxrwxrwx 4 admin        administrators 4096 2022-12-07 17:12 ../
lrwxrwxrwx 1 admin        administrators   34 2022-12-07 17:12 @Recycle -> /share/homes/@Recycle/nathankirwin/
```

E. post the 'id' command output for the userid that isn't working.

```
uid=1000(missethel) gid=1000(missethel) groups=1000(missethel),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),121(lpadmin),135(lxd),136(sambashare),999(plex)
```


Hopefully this is all what you needed. I'm just "okay" with Linux, not great. Patients is appreciated.

---

### Post by TheFu on 2022-12-13
The NFS options in the fstab aren't valid.  I use "nconnect=2,proto=tcp,rw,async" these options from NFSv4 clients.  async and nconnect are not defaults, but the others are.

The 'showmount' command can be run from the client system.  You'll need to point it at the server.   It shows the available options, so it is sorta key to figuring out if the problem is on the client or the server.

BTW, IP addresses aren't any secret.  A NAS should be using a LAN, non-routable IP, so it doesn't matter at all.

The usernames are different between the client and server, can you verify that the uid/gid match?
I fear the directory shown from the client and  on the server aren't the same, since the client is seeing more things than the server holds.  Are you in the correct directory on the server?

---

### Post by BudworthTDog on 2022-12-13
Okay, fstab is a no go, good to know. I think I would like to focus on first getting the share mounted "manually" so to speak in the correct fashion, then I can focus on fstab. Also good thing to know about local ip addresses. 

I ran the showmount command as best I could figure, but Im not sure I'm doing it right because this is what I got back. 

```
showmount --all 192.168.1.93
All mount points on 192.168.1.93:

```

More or less blank, so I'm not sure what's up with that. 

I see what you are saying about the usernames. I was hoping that when I went to mount the share that it would ask me what my username and password are, but it didn't. This could be an issue. How would I go about verifying that the uid/gid match? 

As far as the directory goes I believe I am mounting the correct directory because when I use the following command 

```
sudo mount -t nfs 192.168.1.93:/Public /media/missethel/NFSmountpoint
```

If successfully mounts all the files how I want, in just makes them so they are read only.

---

### Post by BudworthTDog on 2022-12-13
I figured it out. I was so focused on the fact that it worked on my old computer and figured it couldn't be anything on the NAS settings. It was in fact because I needed to input the new ip address of my new computer into the settings on the NAS, silly me. Sorry for wasting your time.

---

### Post by TheFu on 2022-12-13
> **BudworthTDog said:**
> I figured it out. I was so focused on the fact that it worked on my old computer and figured it couldn't be anything on the NAS settings. It was in fact because I needed to input the new ip address of my new computer into the settings on the NAS, silly me. Sorry for wasting your time.

Never a waste of time.   We all do stuff like this.

BTW, I suspect the client location showing the files is just the local disk and by getting the NFS mount onto the directory, you've hidden those files now.

I provided the mount options to put but on the command line and/or in the fstab. You should use those.

NFS isn't CIFS/Samba.  NFS is server-to-server, not user-to-server for authentication.  The only way it knows about different users is via the uid (the number) and the gid (also a number).  On Ubuntu, the first human uid, usually the installer person, is 1000.  The 'id' command shows that.  'id' can take a username arguement to see what other users uid and gids are.  This is all that NFS cares about.

Lastly, if this is really solved, help the community out by using the "thread tools" button near the top of the page and mark it "SOLVED". This saves everyone time.  This would be good one for other people using a NAS to see.

---

