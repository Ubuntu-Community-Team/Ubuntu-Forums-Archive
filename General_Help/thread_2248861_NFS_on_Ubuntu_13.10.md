---
title: "NFS on Ubuntu 13.10"
date: 2014-10-17
forum: General Help
---

### Post by tobias-markus on 2014-10-17
Hey,
Today I installed FreeNas 9.2.1.8 and now I am trying to set up a NFS. First I created a Volume with the volume manager. Then I created a dataset.

Now I want to set up a NFS for this dataset.

So I go to share, add UNIX(NFS) share, as mount point I select the path of my created dataset. As mapalluser and mapallgroup I select nouser and nogroup scince I changed the permission of the dataset to it.
As a final step I have gone to services and switched NFS on.

After that I have installed nfs-common on my client (Ubuntu 13.10) and I now try to mount it with:

sudo mount -t nfs 192.168.1.5:/mnt/Storage/NFS /home/tm/freenas/

It says mount.nfs Connection timed out

On the FreeNAS comes sometimes the message: rpcb_unset failed but I do not know if this has something to do with the Problem.

I am able to ping the freenas server and I tried it also to mount with -o tcp and it did not work.

Additionally I also run the mount command with -v, which get me the following information but I have no clue were the problem is:

```
mount.nfs: timeout set for Fri Oct 17 18:51:20 2014
mount.nfs: trying text-based options 'tcp,vers=4,addr=192.168.1.5,clientaddr=192.168.1.3'
mount.nfs: mount(2): Protocol not supported
mount.nfs: trying text-based options 'tcp,addr=192.168.1.5'
mount.nfs: prog 100003, trying vers=3, prot=6
mount.nfs: trying 192.168.1.5 prog 100003 vers 3 prot TCP port 2049
mount.nfs: prog 100005, trying vers=3, prot=6
mount.nfs: trying 192.168.1.5 prog 100005 vers 3 prot TCP port 897
mount.nfs: portmap query failed: RPC: Timed out
```
When I use the showmount command I get the correct response:
tobias@tobias-ThinkPad-Edge:~$ showmount -e 192.168.1.5
Export list for 192.168.1.5: /mnt/Storage/NFS (everyone

Does anyone know what the problem could be?
Does someone know what the problem here is?

---

### Post by papibe on 2014-10-17
Hi tobias-markus.

I believe it's a DNS/FreeNAS issue. It seems that FreeNAS does a reverse DNS lookup of the client in order to see if it is a valid host.

For what I've read, if you don't have a proper DNS in your LAN, this could be solved by adding the client's host name to the FreeNAS 'hostname database' located on Network ->Global Configuration.

This is just research, I haven't tested myself. Sources [here]("https://forums.freenas.org/index.php?threads/nfs-mount-times-out.7270/") and [here]("https://forums.freenas.org/index.php?threads/nfs-shares-no-longer-mountable.20187/").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by tobias-markus on 2014-10-17
Hey,

Thank you I tried that now but it is not working, the output of the mount -v does not change...

---

### Post by papibe on 2014-10-17
You used the /etc/hosts format right? One line per host, IP and name, e.g.:
```
192.168.1.10  mycurrentclientmachinename
```
After that you may need to restart the NFS service on the FreeNAS machine.

Also try to add these options to the mount command: 'rsize=8192,wsize=8192,timeo=14,intr'

Let us know how it goes.
Regards.

---

### Post by tobias-markus on 2014-10-17
Thank you thats it. I forgot to add the name :)

---

### Post by papibe on 2014-10-17
I'm glad you got it working :D

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Best Regards.

---

