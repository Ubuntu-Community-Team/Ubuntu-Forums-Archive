---
title: "cifs mount error"
date: 2007-12-20
forum: General Help
---

### Post by cujo on 2007-12-20
So, I've googled many times and I cannot come up with a solution to this.

I'm trying to mount a share that is hosted on a Windows 2003 server.  I'm trying to use cifs and I'm running Gutsy.

Here is the command I try...
```
sudo /sbin/mount.cifs //name/of/share /media/share --verbose -o user=fakedomain\fakeusername,pass=fakepassword
```

I know the credentials are correct and the paths are as well.

The output I get is this...
```
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

I have referred to the man page in question.  No help.

I'm really stuck on this one.  Any help would be much appreciated.

---

