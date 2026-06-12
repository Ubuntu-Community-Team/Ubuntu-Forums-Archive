---
title: "[SOLVED] Network Shares... a little help?"
date: 2008-05-29
forum: General Help
---

### Post by EvilMarshmallow on 2008-05-29
Hey all,

I've been trying to find the command to add a network share.  I found the following:

```
sudo mount -t smbfs //fileserver/public /mnt/public -o username=xxxx,password=xxxx
```

When I do this, I get the following:

"mount: wrong fs type, bad option, bad superblock on //fileserver, missing codepage or helper program, or other error..."

I know it can connect to this share, because if I go to the "Location" in nautilus,

smb://fileserver/public

It works fine.

What am I missing?

---

### Post by wootah on 2008-05-29
Looking at the man page, it appears smbmount has been deprecated? It suggested using **cifs**.

Give me a few to check it out.

EDIT: I'm not sure why they say deprecated--it appears you can use it just fine still.

Check out: [http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html]("http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html") this might help out?

---

### Post by wootah on 2008-05-29
The issued command looks perfect though... aside from the obvious (correct username/password) does the mount destination exist?

Gotta cover all bases :)

EDIT: Try this:
```
sudo mount -t cifs //<ip>/share_name /media/my_share -o username=theuser,password=thepass,iocharset=utf8,file_mode=0777,dir_mode=0777
```

(From: [http://www.thatsquality.com/linux/mounting-windows-smb-file-shares-using-cifs]("http://www.thatsquality.com/linux/mounting-windows-smb-file-shares-using-cifs"))

---

### Post by clong83 on 2008-05-29
I think Wootah is on the right path here.  I had a similar problem that drove me nuts for a while.  In general, what I discovered was that the more -o options you give, the better.  Also try listing the workgroup/domain name or even the ip address.  I.E.

```
sudo mount -t smbfs //<ip>/share_name /media/my_share -o username=theuser,password=thepass,iocharset=utf8,file_mode=0777,dir_mode=0777,domain=thedomain,ip=theIPaddress
```

More options can be found by doing a man on smbmount.  These options should work in cifs, too.

---

### Post by wootah on 2008-05-29
> **clong83 said:**
> I think Wootah is on the right path here.  I had a similar problem that drove me nuts for a while.  In general, what I discovered was that the more -o options you give, the better.  Also try listing the workgroup/domain name or even the ip address.  I.E.

```
sudo mount -t smbfs //<ip>/share_name /media/my_share -o username=theuser,password=thepass,iocharset=utf8,file_mode=0777,dir_mode=0777,domain=thedomain,ip=theIPaddress
```More options can be found by doing a man on smbmount.  These options should work in cifs, too.

In specific:
```

man mount.smbfs
man mount.cifs

```

Hope we're getting close here :)

---

### Post by EvilMarshmallow on 2008-05-29
Ok, turns out that IP address and cifs worked...

```
sudo mount -t cifs //ip.address.goes.here/public /mnt/public -o username=xxx,password=xxx
```

This works fine for me.  It wouldn't accept any form of the FQDN... I *had* to use the ip address... and smbfs wouldn't work at all, only cifs.

I noticed in the options, you specified file access levels... does accessing the share in this way override the file permissions that the server has set for the account I log in with?

---

### Post by wootah on 2008-05-29
> **EvilMarshmallow said:**
> Ok, turns out that IP address and cifs worked...

```
sudo mount -t cifs //ip.address.goes.here/public /mnt/public -o username=xxx,password=xxx
```This works fine for me.  It wouldn't accept any form of the FQDN... I *had* to use the ip address... and smbfs wouldn't work at all, only cifs.

I noticed in the options, you specified file access levels... does accessing the share in this way override the file permissions that the server has set for the account I log in with?

Good question:

From man:
> 
dir_mode=arg
          If the server does not support the CIFS Unix extensions this overrides the default mode for directories.

file_mode=arg
          If the server does not support the CIFS Unix extensions this overrides the default file mode.


In the case of using connecting to a Windows share/Samaba, I think using the two options are probably moot. Leaving them off so do you just fine.

Hope that answers things! :)

---

