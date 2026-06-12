---
title: "Mounted SMB Share is Inaccessible"
date: 2006-07-11
forum: General Help
---

### Post by hashstat on 2006-07-11
I have a SMB share I am attempting to mount using smbmount.  The share is accessible in Windows and browsable in Linux using smbclient and gnome.  When I mount the share on the filesystem, however, it is inaccessible.  Trying to ls in the mounted directory results in a "Permission denied" message, even when done as root.  Performing 'ls -l' in the parent directory results in the following list:

```

/mnt$ ls -l
total 0
?--------- ? ? ? ?                ? [COLOR="Red"]share[/COLOR]
```

I used the following command to mount the share (along with several other variations):

```

~$ sudo smbmount //server/share /mnt/share -o username=myusername,ro
```

/var/log/messages and /var/log/dmesg give no clues.  Has anyone seen this before?  What's the fix?

I'm using Samba 3 (3.0.22-1ubuntu3) on Dapper.

Thanks!!

---

### Post by Thund3rstruck on 2006-07-11
is the permission denied coming from windows? Most likely it is. I have had some problems with that in the past. I noticed on my W2K3 server the only way I can mount from Ubuntu to it is by using CIFS. smb tools don't work at all.

mount -t cifs -o crudentials=/etc/cifscruds //Server/Share /media/server

---

### Post by hashstat on 2006-07-11
> **Thund3rstruck said:**
> mount -t cifs -o crudentials=/etc/cifscruds //Server/Share /media/server

That works.  Thanks!!

---

### Post by utherwayn on 2006-07-15
> **Thund3rstruck said:**
> is the permission denied coming from windows? Most likely it is. I have had some problems with that in the past. I noticed on my W2K3 server the only way I can mount from Ubuntu to it is by using CIFS. smb tools don't work at all.

mount -t cifs -o crudentials=/etc/cifscruds //Server/Share /media/server

I was running into the same problems and this line worked for me BUT how do I get it into fstab so it auto mounts?

Edit: Nevermind solved it myself here is the FSTab
//Server/Share	/media/server	cifs	crudentials=/etc/cifscruds	0	0

---

