---
title: "Problem Mounting Windows Network Share"
date: 2007-08-27
forum: General Help
---

### Post by mikaelsnavy on 2007-08-27
I need to a windows network drive at //2k3/home/thinclient, but it will not mount (says it cannot find the remote folder or something). The command I do is "sudo mount -t cifs //2k3/home/thinclient /home/D9LTSP/thinclient -o username=Administrator,password=passadmin,charset=utf8,file_mode=0777,dir_mode=0777". 
I do the same command and I try to mount //2k3/home, it doesn't error out. Is there some way to mount a compound file name like this?
Thanks,
Mikael

EDIT: You cannot do this since //2k3/home/thinclient is not a netowrk share...

---

### Post by jimrz on 2007-08-27
> **mikaelsnavy said:**
> I need to a windows network drive at //2k3/home/thinclient, but it will not mount (says it cannot find the remote folder or something). The command I do is "sudo mount -t cifs //2k3/home/thinclient /home/D9LTSP/thinclient -o username=Administrator,password=passadmin,charset=utf8,file_mode=0777,dir_mode=0777". 
I do the same command and I try to mount //2k3/home, it doesn't error out. Is there some way to mount a compound file name like this?
Thanks,
Mikael

EDIT: You cannot do this since //2k3/home/thinclient is not a netowrk share...

try
```
sudo smbmount //2k3/home/thinclient  /home/D9LTSP/thinclient  -o username=Administrator,password=passadmin,charset=utf8,file_mode=0777,dir_mode=0777
```
think all you need change is "sudo mount" to "sudo smbmount" for your samba mount

---

