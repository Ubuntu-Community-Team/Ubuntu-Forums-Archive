---
title: "shares not mounted anymore at login"
date: 2018-12-24
forum: General Help
---

### Post by alain.roger on 2018-12-24
Hi,

under ubuntu 17.10 i was able to mount shares (from NAS) at the login window using the following lines in the /etc/fstab:

```
//192.168.1.100/storage	/mnt/storage	cifs auto,ver=1.0,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0
```

since i upgraded to ubuntu 18.10 i have mountshare.sh file that includes the following line:
sudo mount -t cifs -o //192.168.1.100/Storage /mnt/storage password=,user=,auto,vers=1.0,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0


but it does not mount the share anyway. Even if i use the commandline "sudo mount -a" to mount it, it does not.

Any idea what do to make it undependent of root and to mount it immediatelly after the login is successful ?

thx

---

