---
title: "fstab smb line error"
date: 2013-01-31
forum: General Help
---

### Post by spacecakes on 2013-01-31
Hi, iam trying to add a smb mount to fstab but it doesnt work. This is the line i got in fstab:
//192.168.1.2/share    /home/random/serverr        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

and this is the error i get:
mount: wrong fs type, bad option, bad superblock on //192.168.1.2/share,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by furything on 2013-01-31
Your fstab entry needs to be in the format
```
mybackend:/media/mediashare /media/mediashare nfs auto 0 0 
```I am assuming this is 2 linux boxes
You should create a dir inside /mnt for your share (you can do other mapping but keep it simple first time) call it remoteServer

for //192.168.1.2/share    /home/random/server should be 
```
192.168.1.2:/full share path /mnt/remoteServer nfs auto 0 0
```

have a look here 
[http://www.mythtv.org/wiki/Mediashares](http://www.mythtv.org/wiki/Mediashares)
I know this is for mythtv but I map /var/lib/mythtv/music this way between 2 linux boxes

---

### Post by spacecakes on 2013-01-31
> **furything said:**
> Your fstab entry needs to be in the format
```
mybackend:/media/mediashare /media/mediashare nfs auto 0 0 
```I am assuming this is 2 linux boxes
You should create a dir inside /mnt for your share (you can do other mapping but keep it simple first time) call it remoteServer

for //192.168.1.2/share    /home/random/server should be 
```
192.168.1.2:/full share path /mnt/remoteServer nfs auto 0 0
```

have a look here 
[http://www.mythtv.org/wiki/Mediashares](http://www.mythtv.org/wiki/Mediashares)
I know this is for mythtv but I map /var/lib/mythtv/music this way between 2 linux boxes

actually its smb between 2 linux boxes because the server box is kind of screwed up and needs to be restarted and iam not in the mode of doing it :) what does the "auto" option mean exactly?

---

### Post by spacecakes on 2013-01-31
it works if i just do username=uname,password=psswd,options but not with credentials :/

---

### Post by furything on 2013-01-31
> what does the "auto" option mean exactly?      Detects the partition type e.g FAT32 ntfs ext 2/3/4

if not working with    credentials then this probably means you have to align user ids and groups between both systems.

On mine I had to use the mythtv account.

do the 
```
id USERNAME
```for the account on both machines I would guess on the samba user as you are doing
/root/.smbcredentials
what is the content of this file or folder?
If folder what is the content of the files? 
It may suggest which account you need.

From link I sent you my understanding is the ids have to match between PCs otherwise yes user and password

---

### Post by steeldriver on 2013-01-31
are you sure you have the cifs-utils package installed?

```
sudo apt-get install cifs-utils
```

> **spacecakes said:**
> 
and this is the error i get:
mount: wrong fs type, bad option, bad superblock on //192.168.1.2/share,
[B]        missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       [/B]In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by furything on 2013-01-31
> are you sure you have the cifs-utils package installed?
very good point

---

### Post by spacecakes on 2013-01-31
> **steeldriver said:**
> are you sure you have the cifs-utils package installed?

```
sudo apt-get install cifs-utils
```

doh, totally missed that, so obvious, thanks for the point, working now :)

---

### Post by steeldriver on 2013-01-31
No problem, actually it's all a bit confusing imho what with samba / smbfs / cifs it's not at all obvious what bits are required

Please mark the thread as SOLVED if you can

---

