---
title: "fstab help with syntax, I can use mount command, fstab says bad line"
date: 2014-02-27
forum: General Help
---

### Post by sdowney717 on 2014-02-27
Windows7 pc is at 192.168.1.7
folder share is 'users/public/Recorded Tv', space issue?????? single quotes work in mount command
machine name is lr
password, there is no password on the windows PC

```

This one works in terminal
sudo mount -t cifs -o username=lr //192.168.1.7/'users/public/Recorded Tv' /mnt

#//servername/sharename  /media/windowsshare  cifs  username=msusername,password=mspassword,iocharset=utf8,sec=ntlm  0  0

This gives bad line in fstab
//192.168.1.7/'users/public/Recorded Tv' /mnt  cifs   username=lr,uid=1000,iocharset=utf8  0  0

```

I am following this wiki, but can not make it work.
I tried the guest line, but also errors in fstab
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by sdowney717 on 2014-02-27
The wiki is incomplete. 
When you have a space, you must put  \040 in its place

this line works

//192.168.1.7/users/public/Recorded\040Tv /mnt  cifs   guest,uid=1000,iocharset=utf8  0  0


Is there a way to tell the article writer about this?
[http://ironman.darthgibus.net/?p=136](http://ironman.darthgibus.net/?p=136)

---

