---
title: "Kerberos &amp; NFS - mount requests failing"
date: 2008-04-17
forum: General Help
---

### Post by scottburton11 on 2008-04-17
Hi all;

I'm trying to share NFS mounts that are Kerberos-authenticated. My directory/authentication server is Apple's Open Directory, and I'm able to kinit, get tickets, view and verify keytab, etc. I've set up the Ubuntu (Gutsy, btw) server according to [https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

Kerberos seems to be set up correctly. The problem comes when I try to mount:

```

pro-tools-3:/mnt admin$ sudo mount_nfs -o sec=krb5i -P xserve7.local:/media/sda1/Installers Installers
mount_nfs: can't access /media/sda1/Installers: Permission denied

```

Server log indicates /media/sda1/Installers isn't exported:
```

Apr 17 14:42:48 xserve7 mountd[11585]: refused mount request from pro-tools-3.foobar.com for /media/sda1/Installers (/): not exported

```

Weird, since:

```

diradmin@xserve7:~$ exportfs -v
/media/sda1/SFX_Library
                192.168.11.10/32(rw,wdelay,insecure,no_root_squash)
/media/sda1/SFX_Library
                192.168.11.100/25(rw,async,wdelay,insecure,root_squash,no_subtree_check)
/media/sda1/Projects
                192.168.11.10/32(rw,wdelay,insecure,no_root_squash)
/media/sda1/Projects
                192.168.11.100/25(rw,async,wdelay,insecure,root_squash,no_subtree_check)
/media/sda1/Sessions
                192.168.11.10/32(rw,wdelay,insecure,no_root_squash)
/media/sda1/Sessions
                192.168.11.100/25(rw,async,wdelay,insecure,root_squash,no_subtree_check)
/home           192.168.11.0/24(rw,async,wdelay,insecure,root_squash,insecure_locks)
/home           192.168.11.10/32(rw,wdelay,insecure,no_root_squash,no_subtree_check)
/media/sda1/Installers
                gss/krb5i(rw,wdelay,insecure,root_squash)
diradmin@xserve7:~$ 

```

it certainly appears that /media/sda1/Installers is exported. 

I've been expecting to see lots of authentication-related errors. With gssd in -vvv verbose logging mode, it's saying absolutely nothing at all - nothing about Kerberos, tickets, nothing - this leads me to believe that nfsd actually hasn't exported this share, even though exportfs says it did. 

Can anyone provide insight here? I'm not much of an NFS admin. TIA.

---

