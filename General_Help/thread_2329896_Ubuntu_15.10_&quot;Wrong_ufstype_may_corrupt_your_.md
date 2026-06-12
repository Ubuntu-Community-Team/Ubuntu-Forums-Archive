---
title: "Ubuntu 15.10 &quot;Wrong ufstype may corrupt your filesystem&quot; Errors."
date: 2016-07-06
forum: General Help
---

### Post by andrew292 on 2016-07-06
Does any one have a fix for the following ?

[1717580.685711] 
[1717580.685711] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
[1717580.685711] 
[1717580.685711] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[1717627.841837] EXT4-fs (xvda2): unable to read superblock
[1717627.844635] EXT4-fs (xvda2): unable to read superblock
[1717627.847308] EXT4-fs (xvda2): unable to read superblock
[1717627.851117] FAT-fs (xvda2): bogus number of reserved sectors
[1717627.865579] FAT-fs (xvda2): bogus number of reserved sectors
[1717627.879642] qnx4: no qnx4 filesystem (no root dir).
[1717627.882485] ufs: You didn't specify the type of your ufs filesystem
[1717627.882485] 
[1717627.882485] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
[1717627.882485] 
[1717627.882485] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old

Ubuntu 15.10 ir-randd hvc0

---

### Post by mörgæs on 2016-07-06
Are you sure it's worth the effort to troubleshoot 15.10 which has less than a month left of support? 

I would suggest a fresh install of 16.04.

---

### Post by andrew292 on 2016-07-06
Thanks for the response Morgs.

I have 4 servers running dual installations of Samba running as file servers with complex file sharing permissions set up using Unix ACLs, each server takes about 2 days to set up, plus there iis the downtime invloved, so i don't want to do that. 

I would consider upgrading to a later version however. 

But it would be much easier just to fix this :( From what i've googled, it's not a serious problem but having said that it still makes me nervous as these are our main company file servers.

Andrew.

---

