---
title: "Permission Problems"
date: 2023-05-23
forum: General Help
---

### Post by paulies on 2023-05-23
Hi,

I have recently acquired a nas server and struggling with the permissions I connect to the server through the other  locations and networks supplying my credentials and everything works treat.

Now when I try to mount the drives they mount fine but with a padlock if I use sudo I can create folders and files etc but no matter what I try I cant give the local account read write access. I have followed
loads of tutorials on what to do how to mount from chmod to chown amongst other but nothing seems to work.

in /etc/fstab I have this

//192.168.0.159/Plex /mnt/nass cifs username=xxx,password=@xxx,rw,vers=3.0,auto, 0 0

The drives mount fine but with read only access I have tried numerous commands but none work.

Any help would be appreciated

---

### Post by TheFu on 2023-05-24
CIFS doesn't support UNIX permissions.  If you want UNIX permission support, use NFS.

BTW, almost any question like this will be so specific to the NAS hardware and OS, that asking here isn't really useful.  You should ask on the NAS vendor's forums ... or better, review their how-to guides which answer questions like this sufficiently for millions of others.

BTW, the fstab line has multiple flaws.  You can only use valid CIFS options and you cannot have a dangling comma at the end.  For CIFS mounts, I use options like this:
```
iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials
```
Putting CIFS credentials into the fstab is a security failure.  Use the credentials= option.  Note, that line above is just the options, not the full like for an fstab file.  I don't put network storage mounts into the fstab. I use **autofs**, but they use the same options.

Again, if you can, use NFS instead.  That has cleaning options and full Unix permission support, natively. The default options should be fine with NFS, assuming your NAS supports it.  BTW, NFS is better for streaming media.  In theory, it shouldn't matter, but if you read the media server forums, you'll see people suggesting that NFS be used on Unix/Linux systems.

---

### Post by paulies on 2023-05-26
> **TheFu said:**
> CIFS doesn't support UNIX permissions.  If you want UNIX permission support, use NFS.

BTW, almost any question like this will be so specific to the NAS hardware and OS, that asking here isn't really useful.  You should ask on the NAS vendor's forums ... or better, review their how-to guides which answer questions like this sufficiently for millions of others.

BTW, the fstab line has multiple flaws.  You can only use valid CIFS options and you cannot have a dangling comma at the end.  For CIFS mounts, I use options like this:
```
iocharset=utf8,rw,vers=2.1,uid=tf,gid=tf,file_mode=0664,dir_mode=0775,credentials=/etc/samba/win7lap-D.credentials
```
Putting CIFS credentials into the fstab is a security failure.  Use the credentials= option.  Note, that line above is just the options, not the full like for an fstab file.  I don't put network storage mounts into the fstab. I use **autofs**, but they use the same options.

Again, if you can, use NFS instead.  That has cleaning options and full Unix permission support, natively. The default options should be fine with NFS, assuming your NAS supports it.  BTW, NFS is better for streaming media.  In theory, it shouldn't matter, but if you read the media server forums, you'll see people suggesting that NFS be used on Unix/Linux systems.

Thankyou for the response I managed to get it working maybe one day Ill understand all this

---

### Post by Morbius1 on 2023-05-29
> **paulies said:**
> Hi,
in /etc/fstab I have this

//192.168.0.159/Plex /mnt/nass cifs username=xxx,password=@xxx,rw,vers=3.0,auto, 0 0

The drives mount fine but with read only access I have tried numerous commands but none work.

Any help would be appreciated

**rw** is redundant since it mounts write-able by default.

**auto** is redundant since it mounts that way by default.

**vers=3.0** may or may not be required. It depends on the version of the Linux kernel you are using. If you are using Ubuntu 20 or beyond you can remove the option. CIFS and the server it's connecting to negotiates the best / highest "vers " to use by themselves.

From man mount.cifs:
> The  default  since  v4.13.5  is  for the client and server to negotiate the highest possible version greater than or
equal to 2.1. In kernels prior to v4.13, the default was 1.0. For kernels between v4.13 and v4.13.5  the  default  is
3.0.
So that leaves us with this:
```
//192.168.0.159/Plex /mnt/nass cifs username=xxx,password=@xxx 0 0
```

The problem now is that although it is mounting writeable it's only writeable to the owner of the mount which is root.

You have many options at this point. One way is to replace root as owner to you:

> //192.168.0.159/Plex /mnt/nass cifs username=xxx,password=@xxx**[COLOR="#B22222"],uid=paulies[/COLOR]** 0 0

You have many other options. 

For example say you only want members of the "plex" group to have write access and everyone else to have read only access. The fstab declarations would look something like this:

```
//192.168.0.159/Plex /mnt/nass cifs username=xxx,password=@xxx,uid=paulies,gid=plex,nounix,dir_mode=0775,file_mode=0664 0 0
```

---

