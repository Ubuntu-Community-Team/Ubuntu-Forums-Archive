---
title: "chown and chmod are not working"
date: 2013-05-23
forum: General Help
---

### Post by 6tr6tr on 2013-05-23
I created a folder: /var/www/test using sudo and now I'm trying to change the owner and permissions, but neither command has any affect. How do I fix this?

```

//None of these do anything
sudo chmod -R 666 /var/www/test/
chown -R myuser:mygroup /var/www/test
chown -R :mygroup /var/www/test
chown -R myuser /var/www/test

```

It just continues to say the owner is root and only root has write permissions!

Using: Ubuntu 10.04

---

### Post by 6tr6tr on 2013-05-23
**WORK AROUND**:

It was a problem with the way I mounted the folder (which is a shared folder from VirtualBox host):

```
sudo mount -t vboxsf test /var/www/test
```

Should have been:

```

#38 is www-data
sudo mount -t vboxsf -o rw,uid=38,gid=38 test /var/www/test
```

This allows my webserver to write to it, but there's still an issue. No  matter who I mounted it under, I was unable to change chown/chmod  afterwards. Is there any way to mount it so it allows changing ownership  and permissions on subfolders and files?

---

### Post by HiImTye on 2013-05-23
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try without specifying a uid or gid

---

### Post by 6tr6tr on 2013-05-23
> **HiImTye said:**
> try without specifying a uid or gid

I tried that but that makes it so only root gets access and I'm unable to change it via chown or chmod.

---

### Post by HiImTye on 2013-05-24
is the shared folder on a windows file system (FAT32/NTFS)? if so that will prevent you from dynamically changing ownership and permissions, since Windows filesystems aren't designed to be *nix friendly

---

### Post by 6tr6tr on 2013-05-24
> **HiImTye said:**
> is the shared folder on a windows file system (FAT32/NTFS)? if so that will prevent you from dynamically changing ownership and permissions, since Windows filesystems aren't designed to be *nix friendly

No, the host is opensuse.

---

### Post by bab1 on 2013-05-25
> **6tr6tr said:**
> No, the host is opensuse.

Does the host use SELinux or  Apparmor?  Or possibly the specific directory might have the immutable attribute set (chattr)?

---

### Post by 6tr6tr on 2013-05-29
> **bab1 said:**
> Does the host use SELinux or  Apparmor?  Or possibly the specific directory might have the immutable attribute set (chattr)?

No to SELinux and apparmor.

The permissions on the folder (in openSUSE):

```
drwxr-xr-x
```

---

### Post by 6tr6tr on 2013-06-03
> **HiImTye said:**
> try without specifying a uid or gid

Just to see, I used a different host computer (a laptop using openSUSE 12.2 instead of 12.1) and created a new VirtualBox guest on that computer with Ubuntu 13.04 (instead of 10.04). I get the same results:

1. Without specifying uid/gid, it gives permission denied

2. With specifying, everything works properly

Why would this be?

---

