---
title: "Mount NFS NAS Synology"
date: 2017-07-31
forum: General Help
---

### Post by red-eagle on 2017-07-31
Hello,

I have just started to work with Ubuntu 16:04. I have a big problem to connect with my NAS.
I am trying to mount my NAS (Synology) through NFS. Ubuntu see the NFS:
   
Eagle@Linux:~$ showmount -e 192.168.x.x

 Export list for 192.168.x.x:

 /volume1/Eagle$ 192.168.x.x

But when i try to mount using:

   

Eagle@Linux:~$ sudo mount 192.18.x.x:/volume1/Eagle$ /mnt/NAS/eagle

 mount.nfs: Network is unreachable

The user name and password are the same on ubuntu as the user on the NAS

What i am doing wrong or what have I forgotten?

---

### Post by steeldriver on 2017-07-31
... possibly just a typo? (192.18 is not the same thing as 192.168)

---

### Post by red-eagle on 2017-07-31
Thnx steeldriver. I feel a little bit stupid now :(

I dont get an error now, but when I go to the map it says that I dont have the rights to look in the map.

---

### Post by steeldriver on 2017-07-31
Since NFS uses UIDs (v3) or username (v4 - I think) you may need to set up an appropriate user mapping if those are not the same on the server and client systems - see for example [UID mapping in NFS](https://unix.stackexchange.com/questions/286924/uid-mapping-in-nfs)

Hope this helps

---

### Post by red-eagle on 2017-07-31
I looked at it. But I dont fully understand. I have put the line [General]

Verbosity = 0
Pipefs-Directory = /run/rpc_pipefs
# set your own domain here, if id differs from FQDN minus hostname
# Domain = localdomain

[Mapping]

Nobody-User = nobody
Nobody-Group = nogroup

[Translation]
Method=static

[Static]
eagle = eagle

But that didnt made any difference.
When I change the squash of nfs on the synology to** Map root to admin **then i can access the files in /mnt/NAS/eagle. It should be NO MAPPING. I am sure now that it is a user/password problem or UID/GID difference between Ubuntu user EAGLE and the  Synology user EAGLE. The password are the same.

By the way I put the following line in /etc/fstab:

192.168.*.*:/volume1/Eagle$ /mnt/NAS/eagle nfs auto,nofail,nolock,tcp,rsize=8192,wsize=8192,timeo=14,intr 0 0 

Do I have to change there something?

---

### Post by red-eagle on 2017-08-02
I found some strange things in the Synology. My uid is 1026. But when I look in the /etc/exports i see that nfs permission is made with user 1025 which is guest. Besides that in etc/idmapd.conf said nobody user = guest instead of nobody.

---

