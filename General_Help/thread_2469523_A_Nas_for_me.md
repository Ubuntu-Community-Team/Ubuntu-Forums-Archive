---
title: "A Nas for me?"
date: 2021-12-01
forum: General Help
---

### Post by josephchrzempiec on 2021-12-01
Hello, I'm working on my first nas for me. I wanted to use ubuntu and I know it will be a little harder because it's not out of the box thing like next cloud or own cloud. But I was wondering What would I need to make a Nas for me. Here are my specs. 

Desktop i3 6100 2 core 4 threads
8GB memory
256 m.2 SSD
2x USB 2TB drives.

It might be a little over kill but this is what I currently have at the moment. I'm not sure what Security I can use and How to raid the two drives together to get redundancy. I do not need speed but I need to not lose my family stuff no more. 

Is there a easy to follow set to do a setup to help someone like me out that is not a programmer?


Joseph

---

### Post by Tadaen_Sylvermane on 2021-12-01
If you want to roll your own I highly encourage it. That being said you will need to do or be willing to do some research. Every setup is unique. What I have may not work for you and vice versa.

At minimum this is what you will need to look for.

Static ip with netplan
Exposing samba and nfs shares to the lan
Ssh access so this box can be headless somewhere it isn't too visible
Raid 1 methods. I personally am using Btrfs at the moment with a pair of 1tb drives for my non media storage. Loving it. Zfs is another option, then the old tried and true mdadm. The first 2 offer bitrot protection.
Look into LVM for the root file system if you use mdadm so you can do snapshots for backups.

Your specs are more than capable of this task and can likely handle other services if you need them. Be aware raid of any kind is not a backup. Prevents downtime. But does not replace proper backups.

---

### Post by ActionParsnip on 2021-12-02
Configure disks then install openssh-server. You now have an SFTP server. Log in with your Ubuntu credentials to authenticate. Done.

---

### Post by HermanAB on 2021-12-04
Yup - even Windows nowadays have OpenSSH.  I simply connect using a file browser and does not use permanent network mounts.

---

