---
title: "Can not mount NAS shared folder anymore"
date: 2020-10-14
forum: General Help
---

### Post by alain.roger on 2020-10-14
Hi,

i have a NAS QNAP where last upgrade has been release on 30.09.2020. 2 days ago, i was still able to sync my desktop with my NAS. My computer runs under Kubuntu 20.04 since 04.2020.
Now, i'm not able to mount NAS shared folders.

Till now i had 2 ways to mount NAS shared folder:
```
QNAP:/wd-6tb-usb /mnt/wd-6tb-usb            nfs auto,nofail,noatime,nolock,intr,tcp,actimeo=1800 0 0
```

or

```
//QNAP/wd-6tb-usb /mnt/wd-6tb-usb    cifs vers=1.0,x-systemd.automount,x-systemd.device-timeout=60,iocharset=utf8,credentials=/home/alain/.smbcredentials,uid=1000,gid=users,file_mode=0775,dir_mode=0775 0 0
```

I know that since kernel 4.13 cifs vers=1.0 is not secured and by default vers2.1 or vers=3.0 should be used, but even if i set this format, nothing works.

I also tried to upgrade Kernel from v5.4 to 5.7 but nothing helps.
Any idea what could be the issue ?
thx

---

### Post by TheFu on 2020-10-14
Seems like a question for the QNAP people.

NFS sorta just works, so simplify that mount and try again. BTW, you probably want
```
QNAP:/wd-6tb-usb /mnt/wd-6tb-usb            nfs  async,intr,proto=tcp 0 2
```

Always check the system log files for error messages.
Also verify that **ping qnap** works. Simple stuff.

You can try to manually mount the storage from a shell.

```
sudo mount.nfs4 -vvv .... 
```
The more 'v's, the more verbose the output.

---

