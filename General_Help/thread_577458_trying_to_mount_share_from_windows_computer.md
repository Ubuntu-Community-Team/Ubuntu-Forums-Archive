---
title: "trying to mount share from windows computer"
date: 2007-10-16
forum: General Help
---

### Post by o2bfishn on 2007-10-16
hey everyone! new to ubuntu, but not linux or debian based distros. i have been using mepis for awhile now and my problem is this. i have a windows pc with a shared drive and in mepis i was mounting the shared drive via the rc.local file with this line in it
```
mount -t smbfs //desktop/share /mnt/share -o rw,user,fmask=0770,dmask=0770,username=user,password=passwd
```

this would mount fine in mepis and then i created links to the folders i wanted in my home directory

now in ubuntu, this does mount the drive but i get permission denied when trying to cd to that directory or browsing to it in gnome, i know i am missing something simple here, any help will be very much appreciated.

---

### Post by o2bfishn on 2007-10-16
anyone?

---

### Post by Tteddo on 2007-10-17
I just had this problem and fixed it with the following command in a shell script.
```
 mount -t smbfs //Warpdrive/Backup /var/Backup -o rw,uid=tteddo,username=tteddo,password=password
```
What got it to work was the uid section. Before that only root could rw to the directory. when it was mounted because root was running the mount command.

---

### Post by maybeway36 on 2007-10-17
Try cifs too, and use that if it works. Otherwise smbfs is still okay.

---

