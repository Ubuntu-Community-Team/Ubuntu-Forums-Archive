---
title: "Interesting NFS issue with 16.04 &amp; 17.04 client"
date: 2017-08-14
forum: General Help
---

### Post by mike.lussier on 2017-08-14
I thought this was a 17.04 issue connecting to a 16.04 system. but it turns out to be an issue on my 16.04 desktop. 



My media-server is running nfs kernel server. 

On my system I just started using my first ZFS array. 

I bind the individual folders on the ZFS to an export directory. i.e. /nfs-exchange/

I have checked the contents of each binding directory & on the ZFS array. I have confirmed that the files are in the correct folders and on the proper binding directory /nfs-exchange/

Here lies the problem, regardless of what I mount. All of the results come back the same. they all have the same contents the TVSHOWS folder. When I mount any other directory such as the Music directory on the client side I see TVSHOWS folders. 

What the heck is going on ?? I have never seen this before. I have never had a problem with actually seeing the directory on any NFS server. out of order maybe but all of the information has been there. in this case I can't do anything right now but look at TV video files. 

manual mounting produces the same results. I went to the desktop that is servuing these files and created a manual mount and it exhibited the same behavior as the remote system. 

mount mediaserver:/nfs-exchange/MUSIC /home/mediaserver/test


[HTML]
<code>
/etc/fstab

# ZFS Drives Bindings
/TVRAID-EXPORT/TVSHOWS        /nfs-exchange/TVSHOWS        none    bind    0    0
/MOVIES-EXPORT/MOVIES           /nfs-exchange/MOVIES        none    bind    0    0
/MASTER-EXPORT/MUSIC            /nfs-exchange/MUSIC        none    bind    0    0
/MASTER-EXPORT/SYSTEM          /nfs-exchange/SYSTEM        none    bind    0    0
/MASTER-EXPORT/PICTURES        /nfs-exchange/PICTURES        none    bind    0    0
/MASTER-EXPORT/DOCUMENTS    /nfs-exchange/DOCUMENTS        none    bind    0    0


/etc/exports

/nfs-exchange/TVSHOWS              192.168.20.0/24(rw,fsid=0,insecure,no_subtree_check,async) 172.18.20.0/26(rw,fsid=0,insecure,no_subtree_check,async)
/nfs-exchange/MOVIES               192.168.20.0/24(rw,fsid=0,insecure,no_subtree_check,async) 172.18.20.0/26(rw,fsid=0,insecure,no_subtree_check,async)
/nfs-exchange/MUSIC                192.168.20.0/24(rw,fsid=0,insecure,no_subtree_check,async) 172.18.20.0/26(rw,fsid=0,insecure,no_subtree_check,async)
/nfs-exchange/SYSTEM               192.168.20.0/24(rw,fsid=0,insecure,no_subtree_check,async) 172.18.20.0/26(rw,fsid=0,insecure,no_subtree_check,async)
/nfs-exchange/PICTURES             192.168.20.0/24(rw,fsid=0,insecure,no_subtree_check,async) 172.18.20.0/26(rw,fsid=0,insecure,no_subtree_check,async)
/nfs-exchange/DOCUMENTS            192.168.20.0/24(rw,fsid=0,insecure,no_subtree_check,async) 172.18.20.0/26(rw,fsid=0,insecure,no_subtree_check,async)

</code>[/HTML]

---

### Post by mike.lussier on 2017-08-15
ZFS should have zero impact on how NFS works. I have never seen a remote mount not match the source like I'm seeing here. 

This is rather interesting. 
in  the /etc/exports file. if I comment out the TVSHOWS and reload NFS then  test a mounting of music then what actually mounts is MOVIES. The next  item in the /etc/export file. 

This is very odd behavior

---

