---
title: "Winxp + samba + share"
date: 2008-06-04
forum: General Help
---

### Post by miickEe on 2008-06-04
Hey

I now can access shared drives on my brother's xp machine after making a rule on his firewall to allow my IP address.

Now I'm trying to share my stuff to him, but it's not working.

I was following this thread:
[http://ubuntuforums.org/showthread.php?t=76647](http://ubuntuforums.org/showthread.php?t=76647)

Having trouble setting up a samba server..

And running this command yielded this error:
```

miickee@miickee-gutsy:~$ sudo mount -t smbfs -o username=miickee,password=miickee,uid=`whoami`,gid=`whoami`,fmask=000,dmask=000  //miickeeserver/miickee /home/`whoami`/Network
[sudo] password for miickee:
25178: Connection to miickeeserver failed
SMB connection failed
miickee@miickee-gutsy:~$ 

```

What's the problem?

---

