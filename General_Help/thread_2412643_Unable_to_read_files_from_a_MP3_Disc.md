---
title: "Unable to read files from a MP3 Disc"
date: 2019-02-15
forum: General Help
---

### Post by heldal2 on 2019-02-15
I create MP3 Discs with "Burn" on a macbook which are unreadable when mounted in ubuntu-studio 18:10. When mounted on the Mac (mojave) all mp3-files on the CD have permissions 0755 (-rwxr-xr-x), but when mounted from ubuntu-studio file-permissions vary between 0327, 0356 and 0320. None of these include read-permission for the user/owner. I have permission to read and execute (cd) the root of the CD in /media/[user] that is created when mounted, but not the individual files within. 

From mount:
```
/dev/sr0 on /media/per/CM Repertoar type iso9660 (ro,nosuid,nodev,relatime,nojoliet,check=s,map=n,blocksize=2048,uid=1000,gid=1000,dmode=500,fmode=400,uhelper=udisks2)
```

These MP3-discs work fine on MacOS, Windows and all MP3-compatible CD-players I have been able to try (car, living-room stereo). In linux OTOH the content can only be accessed with root permissions because file-permissions for some reason get messed up when the disc is mounted.

---

