---
title: "Mount FTP Server - Error: Couldn't resolve host"
date: 2013-02-14
forum: General Help
---

### Post by _user on 2013-02-14
Link: [http://peppoj.net/2012/10/mount-ftp-servers-using-curlftpfs-in-linux/](http://peppoj.net/2012/10/mount-ftp-servers-using-curlftpfs-in-linux/)

I'm trying to replicate the above link.

So I issue the command:

```
curlftpfs [USERNAME]:[PASSWORD]@[FTP-SERVER] [MOUNTPOINT
```

Error:

Error connecting to ftp: Couldn't resolve host 'root'
@XXX.XXX.XXX.XXX: command not found

Where XXX.XXX.XXX.XXX = a real IP.  

The user/password/server-IP are all correct.  Suggestions?

---

### Post by schragge on 2013-02-14
Quote it:
```

curlftpfs [color=red]'[/color]username:password@ftp-server[color=red]'[/color] /mountpoint

```

---

### Post by _user on 2013-02-14
That worked, thanks!

I had an access issue with curlftpfs so went with the preferred method of using sshfs instead:

```
sshfs -o idmap=user user@xxx.xxx.xxx.xxx:/remote/folder /local/mount
```

---

