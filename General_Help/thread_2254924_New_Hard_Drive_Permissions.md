---
title: "New Hard Drive Permissions"
date: 2014-12-01
forum: General Help
---

### Post by hessczoo on 2014-12-01
Hi,

I have set up a new hard drive for server storage. It is mounted at /media/colin/hdd1

I have been trying to get this to work with my Samba sharing and I can't get it to work. Other shares are working fine, but Windows spits out a permissions error. My samba.conf contains;
```

[Test]
path = /media/colin/hdd1
browseable = yes
writable = yes
guest ok = yes
read only = no
create mask = 0755

```

As I said other shares are working fine, so the error isn't in other conf blocks.

I have tried all I can think of, even setting permissions to 0777 doesn't help. Here is the output of ls -l
```
 
drwxrwxrwx 3 nobody nogroup 4096 Nov 30 23:58 hdd1

```

Any suggestions on where to go from here?

Thanks!

---

### Post by yancek on 2014-12-01
Samba is used to share between Linux/windows on a network.  If you have this hard drive attached to your Linux system computer with ntfs filesystems, look into the use of umask, dmask, fmask options.  The standard Linux permissions (0777) aren't going to work on a windows filesystem.  I can't give you any more specifics as I rarely use windows but you should find lots of sites if you do an online search.

---

### Post by hessczoo on 2014-12-01
Hi yancek,

This is an ext4 filesystem, but I don't know if it matters so much in Samba since it is a protocol and the underlying filesystem on the server is never actually touched with the Windows computer. Similar as in HTTP or other serving protocols. 

I have however found that my smb.conf isn't matching up with the output of ```
 testparm -s
```

According to my config I of course have

```

[Test]
path = /media/colin/hdd1
browseable = yes
writable = yes
guest ok = yes
read only = no
create mask = 0755

```

The output of ```
 testparm -s
```

```

[Test]
path = /media/colin/hdd1
guest ok = yes
read only = no
create mask = 0755

```

This is interesting why it is skipping the browseable and writable directives...

---

