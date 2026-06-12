---
title: "POSIX acl over nfs"
date: 2007-06-30
forum: General Help
---

### Post by greg00 on 2007-06-30
**Problem: No extended ACL attributes for files and directories for NFS mounted share.**

I added support for POSIX ACLs on specific partition and new permitions scheme worked like a charm locally and remotely over NFS. The only problem that I yet can't solve is that *getfacl* doesn't show correct permitions for NFS mounted directory.

On server I can see extended acl attributes  ( what a little "+" sighn indicates ) :

```
robot@omega:/public$ ls -ld test
drwxrwxr-x+ 2 robot robot 4096 2007-06-30 22:50 test
```

On client only regular permitions are visible:
```

greg@greg-desktop:~$ ls -ld /net/omega/public/test/
drwxrwxr-x 2 robot 1003 4096 2007-06-30 22:50 /net/omega/public/test/

```

What is interesting that ACL attributes are actually working over NFS !!!


Here is my setup:

**Server side with nfs-kernel-server ( Feisty 7.04 )**

```
greg@omega:~$ mount |grep public
/dev/mapper/vg0-public on /public type ext2 (rw,acl)

```
```
greg@omega:/$ getfacl /public
getfacl: Removing leading '/' from absolute path names
# file: public
# owner: robot
# group: public
user::rwx
group::rwx
other::r-x
default:user::rwx
default:group::rwx
default:group:public:rwx
default:mask::rwx
default:other::r-x

```
**Client side ( Feisty 7.04 )**

```
greg@greg-desktop:~$ mount |grep public
omega:/public on /net/omega/public type nfs (rw,nosuid,nodev,hard,intr,addr=10.0.0.10)

```
```
greg@greg-desktop:~$ getfacl /net/omega/public/
getfacl: Removing leading '/' from absolute path names
# file: net/omega/public
# owner: robot
# group: public
user::rwx
group::rwx
other::r-x
```

Please advice

---

