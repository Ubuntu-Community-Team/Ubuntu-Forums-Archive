---
title: "Need help mounting a Samba share"
date: 2006-08-12
forum: General Help
---

### Post by scratched on 2006-08-12
I just set up a machine in my home as a Debian file server using samba. I'm trying to mount the file on my Ubuntu box, but I can't seem to get it to work.](*,)  

This is how I tried to mount the file, along with the error message I get:

```
sudo mount -t smbfs -o username=xxx.password=xxx //debian/shared /mnt/shared
mount: wrong fs type, bad option, bad superblock on //debian/shared,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

What am I doing wrong here?:-k 

I can see the file using Nautilus and I seem to have no problem using the share directory in Nautilus but I want it to be mounted so I can use it like a regular drive.

EDIT: I just found another post that solved my first error message. All I needed to do was install smbfs by typing "sudo apt-get install smbfs".

Now I get another error message:
```
sudo mount -t smbfs -o username=xxx.password=xxx //debian/shared /mnt/shared
387: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed

```

Could anyone tell me what I might have done wrong?

---

### Post by gerbman on 2006-08-13
I would try following [these]("http://ubuntuforums.org/showpost.php?p=1265314&postcount=2") steps on your Debian machine.

---

### Post by scratched on 2006-08-13
Thanks! That worked perfectly.

---

### Post by gerbman on 2006-08-13
> **scratched said:**
> Thanks! That worked perfectly.You're welcome.

---

