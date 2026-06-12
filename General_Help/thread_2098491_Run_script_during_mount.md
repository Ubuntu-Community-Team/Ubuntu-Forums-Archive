---
title: "Run script during mount"
date: 2012-12-26
forum: General Help
---

### Post by Andruk Tatum on 2012-12-26
Hi, I have a media server all set up with Samba so it can share my movies/TV shows/music to my desktop. I have Samba sharing working perfectly, and I created a script on my server that suspends it if there are no active samba mounts, no terminal users, web browsers not open, and if the last mouse movement was over a timeout period ago.

But, this means that when I fire up my desktop, I'd like it to send a wake-on-lan packet to my server and ping it constantly until it starts to respond (so I know its networking/samba sharing is up) and it is safe to mount the network share. After that is when I want the network share to be mounted.

I am using the following lines in fstab to accomplish the network share mounting:

```

//<server-hostname>/<samba-share> /media/<local-dir>    smbfs   credentials=<cred_file>,_netdev,uid=1000,gid=1000 0	0

```

Is there a trigger I can use to run my wake-on-lan script? Is there a better way to mount the network shares?

Thanks!

---

