---
title: "Mounting cifs shares"
date: 2007-12-21
forum: General Help
---

### Post by psilo357 on 2007-12-21
I am having a problem mounting my NAS.  Every time I try to mount it anywhere i get this error

```
mount error: can not change directory into mount target /randy/music
```

ive tried to mount in two different places and always get the same error...here is how i tried to mount

```
sudo mount -t cifs //STORAGE-0288/Music /randy/music -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

and

```
sudo mount -t cifs //STORAGE-0288/Music /mnt/music -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
```

Thanks for any and all help

peace

---

### Post by psilo357 on 2007-12-23
anyone?

---

### Post by reckless2k2 on 2007-12-23
have you created the mount directories on your ubuntu box?

also, your code needs a little tweaking. you have to specify uid and gid info with cifs. also make sure you have smbfs installed. try code like this which works fine for me:

```
//xx.xx.xx.xx/share /mount/point        cifs    credentials=/root/.smbpasswd,uid=<yourusername>,gid=<yourusergroup>,dir_mode=0775,file_mode=0775     0       0

```

that should do ya fine.

FYI: this is a permanent fstab mount. let me know if you need remount code like everytime mount biz.

---

### Post by psilo357 on 2007-12-24
thanks for the tip man, will try when i get home, I don't have a password on my smb shares, so do i need the credentials?  Also, I know what my uid is obviously, but how do i find my gid?

thanks reckless

peace

---

### Post by Craigus on 2007-12-24
There's a good how-to here: [http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

Mounting without credentials is covered.

---

