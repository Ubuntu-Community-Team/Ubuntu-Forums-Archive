---
title: "No Access to Drive on 14.04"
date: 2014-05-12
forum: General Help
---

### Post by jdmccue927 on 2014-05-12
I recently upgraded from 13.10 to 14.04. I access to a drive on my 14.04 system it was working great on 13.10. I usually do a fstab edit, an nfs share, and a samba share and all is good. not anymore though. I'm trying to open this drive up as wide as possible. I can tighten it down, IF I EVER GET ACCESS arrhhhh! Things tried so far.

fstab:
```
# UUID=***6D7  /TDrive  ntfs-3g auto,users,uid=1000,gid=100,dmask=777,fmask=777,utf8  0

UUID=***6D7  /TDrive  ntfs-3g defaults,user,uid=0,gid=0,umask=777,dmask=777,fmask=777,utf8  0
```

First was default, second is experimentation

Can not even get access locally. Opening in nautlius trsults in: You do not have the permissions necessary to view the contents of “TDrive”.

so I tried to change the permisssions with:

 ```
sudo chmod -R 777 /TDrive
```

and that results in:

```
d---------   1 john users  8192 Mar 14 14:56 TDrive
```

How can giving complete access end up removing access???

Help I need complate control of this drive.

---

### Post by Impavidus on 2014-05-12
From **man mount**:```
       **umask**=_value_
              Set the umask (the bitmask  of  the  permissions  that  are  **not**
              present).  The default is the umask of the current process.  The
              value is given in octal.

       **dmask**=_value_
              Set the umask applied to directories only.  The default  is  the
              umask of the current process.  The value is given in octal.

       **fmask**=_value_
              Set the umask applied to regular files only.  The default is the
              umask of the current process.  The value is given in octal.
```The mask indicates which permissions should **not** be present. To get full permissions, set the mask to 000.

---

