---
title: "mount CIFS and UID option"
date: 2018-11-30
forum: General Help
---

### Post by giobaxx on 2018-11-30
Time to time we use to mount some windows share on the ubuntu box but i still have not clear the user of the option uid and gid to mount Windows Share Folder:

//Server/WindowsShare       /mnt/mount-point cifs **uid=1004,gid=1004**,nofail,credentials=/home/user/.cifscredentials,domain=mydomain 0 0

Sometimes is used sometimes not, could you tell me which is the scope to use the uid,gid to mount a Windows Share?

---

### Post by TheFu on 2018-11-30
The manpage is the clearest description.
```
$ man mount.cifs
... 
       uid=arg
           sets the uid that will own all files or directories on the mounted
           filesystem when the server does not provide ownership information.
           It may be specified as either a username or a numeric uid. When not
           specified, the default is uid 0. The mount.cifs helper must be at
           version 1.10 or higher to support specifying the uid in non-numeric
           form. See the section on FILE AND DIRECTORY OWNERSHIP AND
           PERMISSIONS below for more information.
...
       gid=arg
           sets the gid that will own all files or directories on the mounted
           filesystem when the server does not provide ownership information.
           It may be specified as either a groupname or a numeric gid. When
           not specified, the default is gid 0. The mount.cifs helper must be
           at version 1.10 or higher to support specifying the gid in
           non-numeric form. See the section on FILE AND DIRECTORY OWNERSHIP
           AND PERMISSIONS below for more information.
```

There are many uid/gid options besides those.  But start with the manpage to understand almost all commands.
With CIFS, the owner, group, and permissions for files and directories are controlled only at mount time.  That is the mount of the uid/gid options.  There are also the fmask and dmask settings which address the 32-bit permissions mask.   For most needs.
Inside a business, it might be worthwhile to attempt more fine-grained controls over CIFS ownership, groups, and permissions and not just accept the ocean-level controls that mount options provide.

---

### Post by giobaxx on 2018-12-03
tanks for the help

---

