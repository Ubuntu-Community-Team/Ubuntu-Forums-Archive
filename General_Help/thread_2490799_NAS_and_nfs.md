---
title: "NAS and nfs"
date: 2023-09-16
forum: General Help
---

### Post by hmiersch on 2023-09-16
hello. i recently got my new NAS up and running, installed DSM, created shared folders, all that jazz. the problem is that when i try to connect to it using NFS instead of SMB, i get an error: "unable to access location. mount point does not exist". what do i have to do to get it to work?

---

### Post by yancek on 2023-09-16
The error message is obvious.  Did you create a mount point from the system on which you are trying to access the serve via nfs?

The link below is to the Ubuntu site on setting up after installing nfs.  I'd suggest reading through it and comparing instructions to what you did.

 [https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs)

---

### Post by SeijiSensei on 2023-09-16
Also you'll need to install the "nfs-common" package if you haven't done so already. It is not included by default in Ubuntu but is necessary on NFS clients.

---

### Post by hmiersch on 2023-09-16
>  Also you'll need to install the "nfs-common" package if you haven't done so already   i've done that, and then i tried to follow the instructions in [https://ubuntu.com/server/docs/service-nfs](https://ubuntu.com/server/docs/service-nfs) but it is quite confusing. for example, it tells me to  ```
 sudo mount example.hostname.com:/srv /opt/example  
```. if i use that method, do i have to mount the NAS every time i boot my computer?  i tried this: ```
 sudo mount ds423:/Backups  /opt/example 
``` and i got an error: ds423:/Backups can't find in fstab.   what i want to do is make backups of my ubuntu HD with the backups app and store them on the NAS, and i don't want to use SMB because of its restrictions.

---

### Post by yancek on 2023-09-16
If you want it mounted on boot, you need an entry in fstab.  You can find many sites with example entries.  One posted below which you will have to modify with the correct IP (Not 192.168.0.32), the directory being exported(/home/bob) and the mount point (/mnt/seagat)on your computer to make it accessible.

```
 192.168.0.32:/home/bob /mnt/seagate nfs rw,defaults 0 0
```

---

### Post by SeijiSensei on 2023-09-16
You also need to create an empty directory at /opt/example. This becomes the "mount point" for the remote server. /opt/example is probably not where you want to mount this. I follow the Ubuntu convention of using /media for all mount points. You probably want to create something like /media/Backups as the mount point.

```

sudo mkdir /media/Backups

```

Next, it looks like Linux can't assign an IP address to the name ds423. The simplest solution to this is to edit (as root with sudo) the file /etc/hosts and add a line like
```

1.2.3.4     ds423

```
using the machine's actual IP address.

Then you can use 
```
sudo mount ds423:/Backups /media/Backups
```

If that works, add an appropriate line to /etc/fstab as hmiersch recommends above.

---

### Post by hmiersch on 2023-09-17
i created that directory and added ds423: to my hosts file, and then i said:  ```
 sudo mount ds423:/Backups/Ubuntu /media/Backups --rw
``` and mount gave me the following error:  "mount.nfs: access denied by server while mounting ds423:/Backups/Ubuntu"  so what settings do i need to activate on my synology NAS? NFS is active, of course.

---

### Post by SeijiSensei on 2023-09-17
Did you export Backups/Ubuntu or just Backups? If the latter, you must mount that.

Also I assume you didn't add a hosts entry for "ds423:" but just "ds423".

Finally, you can use the -v switch to get more verbose output from mount. Try "sudo mount -vvv ...".

You might also be encountering a versioning issue. If the NAS runs NFS3, try using

```
sudo mount -o nfsvers=3 ds423: ...
```

You should see versioning problems if you use -vvv.

Also there is no --rw option to mount as far as I know. (See "man mount" for details.) Access is generally controlled by the server. Options are passed to mount with the -o switch as in the previous example.

---

### Post by hmiersch on 2023-09-17
>  Did you export Backups/Ubuntu or just Backups? If the latter, you must mount that.   on my nas i have a folder called Backups which contains 2 more folders called Ubuntu and HomeAssistant. i tried mounting /Backups instead of /Backups/Ubuntu, with the same result.   >  Also I assume you didn't add a hosts entry for "ds423:" but just "ds423".   correct. should i add one for ds423: ?  >  Finally, you can use the -v switch to get more verbose output from mount. Try "sudo mount -vvv ...".   i'll have to try that.  >  You might also be encountering a versioning issue. If the NAS runs NFS3, try using The NAS can do NFS 2, 3, 4 or 4.1.

---

### Post by TheFu on 2023-09-17
On the NAS, you must "export" the directory.  I don't have any experience with home NAS devices, but for Unix/Linux that would be handled by adding a line to the /etc/exports file on the NFS server, then restarting the NFS server daemon.

On the client side, you can use the fstab or a mount command.  Name resolution is required to find the NFS server if you don't want to use the IP address.  A few rules:
[LIST]
[*] the IP for the NFS server should be static.
[*] the mount point (usually an empty directory) must pre-exist on the client
[*] the firewall on the server needs to allow the NFS port(s).  I think there are 3 for NFSv4. One of those ports isn't fixed, unless you force it to be fixed, which I do to make the firewall entry possible.  NFS ufw rules:
```
2049    ALLOW  172.22.22.0/24  # NFS
13025   ALLOW  172.22.22.0/24  # RPC mount option
111     ALLOW  172.22.22.0/24  # portmapper 
```[/LIST]

No need to any options, usually.
```
 sudo mount -t nfs  {ip}:/{export directory location on server}  /{client-side mount point}
```
[LIST]
[*]NFS clients and servers negotiate the protocol used.
[*]NFS clients and servers negotiate the size of data windows used.
[*]NFSv4 uses tcp by default. This is a good thing. Older versions of NFS use udp by default, because they were designed when we had 10 baseT networks and the overhead of TCP was noticeable.  With GigE networks, tcp should be used for any version of NFS.  v4.x NFS has been around over 20 yrs, BTW. It isn't new.  v4.2 is a few years old, but NFS is so great because it is backward compatible and they have a migration for when installed versions don't quite match.  Wish other tools were like that (looking at you rdiff-backup!).
[/LIST]

For NFS and other sometimes gone storage (like USB), I prefer to use the **autofs** method for mounting.  This way, mounts only happen when required.  It makes dealing with an NFS server that isn't booted nicer, assuming no process demands it be connected.  Having a system lock up because the NFS server isn't working sucks.

---

