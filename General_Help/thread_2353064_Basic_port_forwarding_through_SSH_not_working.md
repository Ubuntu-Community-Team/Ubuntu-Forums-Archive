---
title: "Basic port forwarding through SSH not working"
date: 2017-02-18
forum: General Help
---

### Post by Gottier on 2017-02-18
Local machine is Ubuntu 14.04 desktop with LAMP (MariaDB on port 3306). Remote machine is unknown linux LAMP type server accepting SSH connections on port 2233.

So I do this in terminal:

```
ssh -L 3307:xxx.xxx.xxx.xxx:3306 -p 2233 me@remoteserver.com -N
```

But when I try to connect to the remote server MySQL (127.0.0.1 and port 3307) it is obvious that I am getting errors from local MariaDB. I say this because if I stop MariaDB on the local machine, the error messages change.

I do get a prompt on the remote server if I leave off the -N, and I can connect with a standard SSH connection just fine. Are there things to look for that would be holding back the port forwarding? Is my command right?

---

### Post by TheFu on 2017-02-19
Are you using ssh-keys?
-f option might be needed if a password is needed.  I looked at the ssh manpage and it isn't exactly clear. Also, might want to use the ~/.ssh/config file to handle the non-standard port and different username.  Makes life a little easier, though I don't see anything directly wrong.

I assume you've tested that regular ssh into the machine works? It isn't clear from the post.
Anything interesting in the log files or when using ssh -vvv options?

---

### Post by Gottier on 2017-02-19
The answer was here:

[https://ubuntuforums.org/showthread.php?t=2233799&p=13073306#post13073306](https://ubuntuforums.org/showthread.php?t=2233799&p=13073306#post13073306)

---

