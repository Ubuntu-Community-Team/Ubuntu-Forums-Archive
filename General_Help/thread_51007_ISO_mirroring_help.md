---
title: "ISO mirroring help"
date: 2005-07-22
forum: General Help
---

### Post by xgregx on 2005-07-22
Hello all, 
I'm trying out Ubuntu and really like it, so I want to help by hosting a mirror.  I've rsync'd against the releases mirror, and I'm getting about 9 GB of data, but all the links are broken.  Here is some output from du:
```
cs@ghweb01 ubuntu $ du -h 5.9G    ./.pool
353K    ./hoary
16K     ./jigit
409K    ./warty
3.6G    ./kubuntu/.pool
361K    ./kubuntu/hoary
3.6G    ./kubuntu
4.0K    ./.trace
9.4G    .
``` 

As you can see most of the stuff is going into that ".pool" directory.  Here is my rsync command I'm using:

```
rsync --recursive --stats --progress --perms --delete -cR rsync://releases.ubuntu.com/releases/ .
``` 

The server is not an Ubuntu box.  Let me know what I might be doing wrong.

Can anyone help?  Thanks! 
Greg :)

---

