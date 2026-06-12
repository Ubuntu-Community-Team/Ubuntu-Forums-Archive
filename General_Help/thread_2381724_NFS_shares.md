---
title: "NFS shares"
date: 2018-01-04
forum: General Help
---

### Post by Kedster on 2018-01-04
Hello,
I have Ubuntudesktop setup as a personal home server. What I am currently trying to achieve is to set up lakka (on a raspberry pi) and a few laptops to share roms and saves through NFS on my server. I have NFS set up and working, both for this and general network file access. 
lakka (and most Raspberry pi distros) operate as root, the problem I have run into is that now when lakka creates files on the NFS share they are owned by root and therefore read only on all other systems including the server(unless root/sudo).

My question is Is there a way to either 
1) force all files created on an nfs share to have certain permissions even if created by another system/user

2) force lakka to write its files as a basic user

---

### Post by Kedster on 2018-01-04
I did a lot of research and I have solved the problem. the resolution is actually quite simple and its host side so easy to do. I added
```

all_squash,anonuid=1000,anongid=100
```
to the share options in /etc/exports and now all users on the NFS make files as a regular user. This allows everything to be accessed by all users on each system.

For any future readers, using all_squash turns ALL interactions into the desired user. (user 1000 group 100, in my case) but this gives ANYONE these rights, if you are working in anything bigger then a trusted home network please use root_squash instread(it is actually default) a as this converts all root user requests only (in effect lowering their rights) and be sure to set anonuid and anongid to what you want(it could even be root if you wanted) but for my purpose of being on my homenetwork and accessing from multiple trusted pc's I have used all_squash to regular user seemed the best solution.

---

### Post by jbamford92 on 2018-05-20
> **Kedster said:**
> I did a lot of research and I have solved the problem. the resolution is actually quite simple and its host side so easy to do. I added
```

all_squash,anonuid=1000,anongid=100
```
to the share options in /etc/exports and now all users on the NFS make files as a regular user. This allows everything to be accessed by all users on each system.

For any future readers, using all_squash turns ALL interactions into the desired user. (user 1000 group 100, in my case) but this gives ANYONE these rights, if you are working in anything bigger then a trusted home network please use root_squash instread(it is actually default) a as this converts all root user requests only (in effect lowering their rights) and be sure to set anonuid and anongid to what you want(it could even be root if you wanted) but for my purpose of being on my homenetwork and accessing from multiple trusted pc's I have used all_squash to regular user seemed the best solution.

It depends. Recommend using Static IP's if you havent already. I use the following for my NFS Shares on my Server.

This is just a example.
var/jackbamford/Storage 192.168.1.2(rw,sync,no_subtree_check)
/home 192.168.1.2(rw,sync,no_root_squash,no_subtree_check)


/var/jackbamford/Storage 192.168.1.10(rw,sync,no_subtree_check)
/home 192.168.1.10(rw,sync,no_root_squash,no_subtree_check)


/var/jackbamford/Storage 192.168.1.11(rw,sync,no_subtree_check)
/home 192.168.1.11(rw,sync,no_root_squash,no_subtree_check)

---

