---
title: "gvfs-mount doesn't perserve the correct timestamp on files"
date: 2013-06-01
forum: General Help
---

### Post by apollothethird on 2013-06-01
Can someone advise me of a way to have gvfs-mount preserve the correct file timestamp?

I originally noticed this when mounting my Samsung Android phone and copying files between my PC and the phone.  I first thought it was a bug in the ftp app.  However, I just tested it by mounting a normal ftp from a Ubuntu machine.  The timestamp isn't preserved there either.

I know there are other ftp clients that I can use, but I was trying to do this with gvfs-mount, because it has the convenience of using the user's space without having to use sudo on the resource.

Since gvfs appears to be such a standard of Nautilus, I would think there might be resolutions for this... hopefully something simple, that I'm just failing to see.

You can test it by running the following two commands and looking at the timestamp of the files:

Using ftp (look at the timesstamp);
```

$ ftp ftphost
Name: [username]
Password: [password]
ftp>ls -l

```

Using gvfs-mount:
```

$ gvfs-mount ftp://ftphost
User: [usrname]
Password: [password]
cd /var/run/user/ljames/gvfs/ftp\:host\=ftphost
ls -l

```

Thanks in advance for anyone who has some input on this.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/~ljames")

---

