---
title: "Strange automount problem with remote windows machine"
date: 2007-09-03
forum: General Help
---

### Post by opus1 on 2007-09-03
I have a windows machine that is running w2k and contains most of my documents (largest hard drive in the network).  I followed a couple tutorials and got a Debian file server working with automount, but when I tried to do the same with the windows box, nothing happens!

Here's the details:  I'm running dapper and trying to access a w2k partion.

I can successfully mount the w2k partition with:

```
sudo mount -t cifs //xxx.xxx.x.x/d$ /home/user/MyDocs  -o user=xx,pass=xx,domain=xx
```

Here's what I put in the auto.master file:

```
/windoze /etc/auto.windoze --timeout=60
```

Here's what's in the auto.windoze file:```


windocs -fstype=cifs,rw,noperm,user=xx,pass=xx ://xxx.xxx.x.x/d$
```

I have a "windoze" directory.  When I issue a mount command it says:

```
automount(pid4613) on /windoze type autofs (rw,fd=4,pgrp=4613,minproto=2,maxproto=4)

```

how ever when I open a terminal and go to the "windoze" directory and do an "ls" I get nothing.  repeatedly.  

Like I said, I was able to get a Debian file server to work using the same set up.  There must be a windows 'thing' that I'm missing, but I can't find a tutorial that tells me anything different than what I did above.

If anyone could help it would be nice.  I can mount these manually, but it would be handy to have automount working.

Thanks.

---

### Post by opus1 on 2007-09-08
Any ideas out there?

---

