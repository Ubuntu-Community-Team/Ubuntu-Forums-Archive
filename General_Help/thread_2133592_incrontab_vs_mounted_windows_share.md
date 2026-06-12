---
title: "incrontab vs mounted windows share"
date: 2013-04-08
forum: General Help
---

### Post by zero2infinity on 2013-04-08
I am trying to setup an Ubuntu box to monitor a Windows share folder and execute a script when a file is moved into the folder. I am using incrontab to do this, but I cannot get it to recognize when a file is dropped into the folder from a Windows machine. If I drop a file in folder from the Ubuntu box, the incrontab sees it and excutes the script perfectly.

I've run inotifywait -m on the folder, and get no output from the Windows side, and the expected output from the Ubuntu side.

So I guess what I need to know, is Linux capabe of monitoring a Window sfolder for changes and launching a script when they are detected?

Thanks!

The Windows network share is mounted via fstab:

//aohome/home/netscans/pdf /media/pdf cifs domain=OURDOMAIN,credentials=/home/manager/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

