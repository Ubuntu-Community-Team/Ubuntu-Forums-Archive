---
title: "How to get NFSv3 working"
date: 2006-12-03
forum: General Help
---

### Post by wilso027 on 2006-12-03
I am trying to stream files larger than 2GB over from an Edgy NFS server. I think all my client are connecting as NFSv2 client instead of NFSv3. I tried to tell the clients to use NFSv3 in the options but if I did that it would not mount. Do I have to modify something to make nfsv3 work on Edgy? Here is what made me think server is set to NFSv2 running nfsstat:

> Server nfs v2:
null         getattr      setattr      root         lookup       readlink
29        0% 4235      3% 2         0% 0         0% 203       0% 0         0%
read         wrcache      write        create       remove       rename
123491   96% 0         0% 0         0% 0         0% 0         0% 0         0%
link         symlink      mkdir        rmdir        readdir      fsstat
0         0% 0         0% 0         0% 0         0% 20        0% 31        0%

Server nfs v3:
null         getattr      setattr      lookup       access       readlink
9264    100% 0         0% 0         0% 0         0% 0         0% 0         0%
read         write        create       mkdir        symlink      mknod
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
remove       rmdir        rename       link         readdir      readdirplus
0         0% 0         0% 0         0% 0         0% 0         0% 0         0%
fsstat       fsinfo       pathconf     commit
0         0% 0         0% 0         0% 0         0%


Thanks for any help I have been stuck on this for a while.

Allan

---

### Post by wilso027 on 2006-12-04
I ended up skipping NFSv3 and going straight to NFSv4. I wrote an article in the mythtv wiki if it helps anyone else out.

[http://www.mythtv.org/wiki/index.php/NFSv4_on_Edgy]("http://www.mythtv.org/wiki/index.php/NFSv4_on_Edgy")

Allan

---

