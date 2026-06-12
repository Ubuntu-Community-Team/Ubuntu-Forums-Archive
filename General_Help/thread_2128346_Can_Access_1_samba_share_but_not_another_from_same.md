---
title: "Can Access 1 samba share but not another from same source on a ubuntu 12.04 client"
date: 2013-03-22
forum: General Help
---

### Post by snuffy47 on 2013-03-22
I am completing scratching my head.

Had hardware failure on my server and now have 12.04 installed and have reassembled my Raid drives

Now I have setup samba how I remeber it and I can connect from a Ubuntu Computer to the 1tbdisk2 share with user dsmc but can not access the serverraidmovies share.  It asks for the username-domain and password but will no accept pw and says not accessible.  the 1tdisk(nfts) share is just 1 hrd drive and the serverraidmovies share is on my raid 6 array(ext4)

UPdate:  I have also noticed that both these drives are owned by root.  I went to change the 1tbdisk(NFTS) drive to the adimn user and it keeps going back to root,  I can change the Raid Drive from root if need though by the looks of it.  I chmod 777 the raid drive also

any help here would be greatly appreciated been at it a few days now

Update

I changed fstab for ext4 drive


/dev/sda8    /media/foo    ext4    rw,user,exec,umask=000 0 0

found here
[http://superuser.com/questions/174776/modify-fstab-entry-so-all-users-can-read-and-write-to-an-ext4-volume](http://superuser.com/questions/174776/modify-fstab-entry-so-all-users-can-read-and-write-to-an-ext4-volume)

I have no idea how I go tlooking here or reason for trying it but it seemed to fix the problem

```
#======================= Global Settings ===================================== [global]
    workgroup = HOME
    server string = SmithsServer
    netbios name = SmithsServer
    security = user
    encrypt passwords = yes
    win support = yes
    map to guest = bad user
    dns proxy = no
    username map = /etc/samba/smbusers








#============================ Share Definitions ============================== 
[1tbdisk2]
    path = /mnt/1TB_Disk2
    browseable = yes
    writeable = yes
    comment = 1tbdisk
    valid users = smithsserver, trevorsmith, dsmc


[serverraidmovies]
    path = /mnt/ServerRaid6_1/Movies
    browseable = yes
    writeable = yes
    comment = Server Raid Movies
    valid users = dsmc


[serverraid61]
    path = /mnt/ServerRaid6_1
    browseable = yes
    writeable = yes
    comment = Server Raid 6 1
    valid users = dsmc, smithsserver, trevorsmith
```

---

