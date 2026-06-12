---
title: "Error Setting Permissions, No such File or Directory on CIFS mount"
date: 2014-02-22
forum: General Help
---

### Post by dannyboy79 on 2014-02-22
I have a Western Digital My Book World Edition which shares via the smb protocol and I recently installed Xubuntu 13.10 and am using the same exact fstab entry to mount the share as I was from my previous Xubuntu 12.04 install BUT now I am receiving the following error dialog box BUT what's weird is that it's still writing the file
[IMG]https://lh3.googleusercontent.com/-I_X65DeDz8o/UxORwH3L5sI/AAAAAAAACks/lc5NBO_g7_U/s374/error%2520writing%2520permissions.png[/IMG]
The fstab entry is the following
```
//192.168.0.50/public	/mnt/circle	cifs	users,_netdev,noauto,noexec,username=daniel,password=,nounix,uid=1000,gid=1000,sec=ntlm,iocharset=utf8,file_mode=0777,dir_mode=0777	0	0
```

Can anyone help me with this, it must be something new in Ubuntu 13.10 because as I said I didn't get this error in 12.04

---

