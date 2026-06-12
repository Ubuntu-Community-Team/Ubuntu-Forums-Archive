---
title: "Mounting remote ubuntu smb share to local ubuntu system"
date: 2015-09-12
forum: General Help
---

### Post by zach39 on 2015-09-12
I've been through a few of the other threads, most of which seem to be detailing how to permanently mount a windows share to your Ubuntu box. 

I am looking to mount 2 SMB shares on one of my ubuntu servers /home/username/movies1 and /home/username/movies2 to my other ubuntu server.

Any assistance would be greatly appreciated.

[http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/)

This is one post I've been following, but it is another one that seems to be exclusively about windows shares.

---

### Post by bab1 on 2015-09-12
> **zach39 said:**
> I've been through a few of the other threads, most of which seem to be detailing how to permanently mount a windows share to your Ubuntu box. 

I am looking to mount 2 SMB shares on one of my ubuntu servers /home/username/movies1 and /home/username/movies2 to my other ubuntu server.

Any assistance would be greatly appreciated.

[http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/08/map-network-drive-onto-ubuntu-14-04/)

This is one post I've been following, but it is another one that seems to be exclusively about windows shares.
I don't like that tutorial.  It has errors in it.  It doesn't matter whether it is a windows machine or an Ubuntu machine.  Both are mounted the same in fstab.  This is basically how you do it```
//COMPUTERNAME/share-name/   /path/to/mount/point  cifs  username=<your-name>,password=<your-password>,gid=1000,uid=1000,iocharset=utf8,sec=ntlm  0  0
```

I would read this: [https://wiki.ubuntu.com/MountWindowsSharesPermanently]("https://wiki.ubuntu.com/MountWindowsSharesPermanently")**** 

and this:[http://askubuntu.com/questions/157128/proper-fstab-entry-to-mount-a-samba-share-on-boot]("http://askubuntu.com/questions/157128/proper-fstab-entry-to-mount-a-samba-share-on-boot")

Do you have a specific question that you need answered or topic you don't understand?

---

