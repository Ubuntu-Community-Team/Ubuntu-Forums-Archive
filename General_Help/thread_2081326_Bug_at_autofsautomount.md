---
title: "Bug at autofs/automount?"
date: 2012-11-06
forum: General Help
---

### Post by absoord on 2012-11-06
Hi people!

I'm really stucked with such a simple thing like configuring autofs5 on Ubuntu Precise using 3.2.0-26-generic-pae kernel.

Remotely I have a samba server which I want to access from a client.

On the client side, I installed autofs:

```

# apt-get install autofs

```

In /etc/auto.master I added the following line:

```

/mnt/shared   /etc/auto.shared   --timeout=60

```

Content of auto.shared is:

```

shared   -fstype=cifs,uid=localuser,gid=localuser,iocharset=utf8,credentials=/etc/credentials,nosetuids,noperm   ://192.168.0.99/shared

```

I'm pretty sure the /etc/credentials file has the right credentials.

After this, I restarted autofs and directory /mnt/shared exists but it's empty...

```

root@monitorize:/mnt/shared# ll
total 4
drwxr-xr-x 2 root root    0 nov  6 19:22 ./
drwxr-xr-x 3 root root 4096 nov  6 19:22 ../

```

On the server side this directory has a lot of files. Curiously using smbclient I can connect to the remote server and I see the files (using the same credentials file). Even mounting manually or via fstab this samba-point it works properly. It's just autofs/automount that fails... Absolutely nothing in the logs. I tried to teardown apparmor and didn't work, and also to find something about this but I didn't see any relevant, nor in this forum, what makes me think this can be some kind of bug.

Also tried to specify manually username and password parameters in auto.shared, and still doesn't work.

Any ideas about this?

Thanks a lot!

---

### Post by papibe on 2012-11-06
Hi absoord.

Since you are using an indirect map you should just reference '/mnt' on the master and 'shared' on the indirect map.

As for now, I think your are mapping /mnt/shared/shared.

Could you try this:
```
cd /mnt/shared/shared 
```
Let us know how it goes.
Regards.

---

### Post by absoord on 2012-11-06
First off, thanks for your reply!

The command you wrote doesn't work:

```

root@monitorize:~# cd /mnt/shared/shared
bash: cd: /mnt/shared/shared: No existe el archivo o el directorio

```

I knew it's mapped this way but I can't access it... also tried it just referencing /mnt in the master and doesn't work either. So weird...

---

### Post by papibe on 2012-11-06
I just test your settings, and they work on my system.

I just had to replace localuser, localuser for the actual values (in my case 1000 and 1000).

Are you using those literally or are you hiding the actual values you are using?

Regards.

---

### Post by absoord on 2012-11-06
Both user and group exist:

```

root@monitorize:/mnt# cat /etc/passwd | grep localuser
localuser:x:1002:1002::/home/localuser:/bin/sh

root@monitorize:/mnt# cat /etc/group | grep localuser
localuser:x:1002:

```

I'm also confused since I've also reproduced this same configuration in other Ubuntu systems and it worked... I don't know what am I doing wrong now!

Thanks again!

---

### Post by papibe on 2012-11-06
Don't use the names, use the number values, i.e., 1002 for both.

---

### Post by absoord on 2012-11-06
Still the same :-(

I could give an additional step... I found out there's one message in the syslog related with automount:

```

Nov  6 20:40:24 monitorize automount[27553]: syntax error in nsswitch config near [ syntax error ]

```

Researching a bit about this it looks like a bug...

[https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/488696](https://bugs.launchpad.net/ubuntu/+source/autofs5/+bug/488696)

None of the solutions have worked for me, so I guess I'll have to wait for the official package fix...

Thanks for the help!

---

### Post by papibe on 2012-11-06
Another difference was that my credential file is in my home directory (I used 10.04 btw)

---

