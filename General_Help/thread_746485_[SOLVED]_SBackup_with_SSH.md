---
title: "[SOLVED] SBackup with SSH"
date: 2008-04-05
forum: General Help
---

### Post by tamoneya on 2008-04-05
I have install SBackup and like it a lot so far.  I have been attempting to do the backups over SSH to my server.  I told SBackup to back up to ssh://tamoneya:_my_password_@tamoneya.homelinux.org/media/disk/Backup.  When I run a test on that it says "The selected destination is not writtable with current permissions.  The backups can not be written there.  The permissions of /media/disk/Backup are ```
drwxrwxrwx  5 tamoneya tamoneya  4096 2008-04-05 07:47 Backup
``` so i dont see why there should be any permissions errors.  

I know that the ssh server is working since I am able to ssh into it with that user name and password and i am able to ```
touch /media/disk/Backup/test
```.

I was reading several other posts in the forums about trying ```
sudo rm /root/.ssh/known_hosts
```  This however has not worked for me like it did for everybody else.  I tried this command on both the server and the client computer and I attempted to ssh into the server before and after running this command and had no trouble either time.

---

### Post by tamoneya on 2008-04-06
my problem seems to be that I had the wrong port number since I changed it on my computer
```
ssh://tamoneya.homelinux.org:42/media/disk/Backup
```

---

