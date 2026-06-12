---
title: "umount fail"
date: 2005-10-30
forum: General Help
---

### Post by earobinson on 2005-10-30
```
earobinson@null:/media/cdrom$ umount /media/cdrom
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
earobinson@null:/media/cdrom$ umount -f /media/cdrom
umount: only root can do that
earobinson@null:/media/cdrom$ sudo umount -f /media/cdrom
Password:
Sorry, try again.
Password:
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
```


any ideas?

---

### Post by heimo on 2005-10-30
Change current working directory to some other place before umounting, check open files with ```
lsof|grep cdrom
``` close programs / files, try again, use -v flag to get more information.

---

### Post by xmastree on 2005-10-31
[QUOTE=earobinson]```
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
```
any ideas?[/QUOTE]What were you doing with the CD?
I've had this problem with firefox opening a file on a CD. Even though it's no longer using the file, the fact that firefox was still running made the system think the CD was in use.
Closing firefox enabled me to eject the CD.

---

### Post by earobinson on 2005-10-31
I played a movie off it using xine (then closed xine)

```
earobinson@null:/media/cdrom$ lsof|grep cdrom
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.

```
(Dont think it worked)

---

### Post by heimo on 2005-10-31
[quote=earobinson]I played a movie off it using xine (then closed xine)

```
earobinson@null:/media/cdrom$ lsof|grep cdrom
lsof: WARNING: can't stat() ext3 file system /dev/.static/dev
      Output information may be incomplete.

``` (Dont think it worked)[/quote] 
Gives me the same warning, but otherwise seems to work fine, so there probebly were no open files in any of your /media/*cdrom* directories. Still not umounting? Any info with -v?

EDIT: Check that xine quit properly, killall xine or killall gxine to make sure.

---

### Post by earobinson on 2005-10-31
```
earobinson@null:/media/cdrom$ sudo umount -f /media/cdrom
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
earobinson@null:/media/cdrom$ sudo umount -fv /media/cdrom
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
earobinson@null:/media/cdrom$ sudo umount -v /media/cdrom
umount: /media/cdrom0: device is busy
umount: /media/cdrom0: device is busy
```

```
earobinson@null:/media/cdrom$ su
Password:
root@null:/media/cdrom#
root@null:/media/cdrom# killall xine
xine: no process killed
root@null:/media/cdrom# killall gxine
gxine: no process killed
```


I can solve this with a ctrl alt backspace, or a reboot (it has happened before) but I would like to find a real soultion

---

### Post by heimo on 2005-10-31
How about:
```
cd /tmp
sudo umount /media/cdrom

```

---

### Post by earobinson on 2005-10-31
[QUOTE=heimo]How about:
```
cd /tmp
sudo umount /media/cdrom

```[/QUOTE]
Worked, may I be so bold as to ask why it worked?

Thanks for all the help

---

### Post by heimo on 2005-10-31
Your current working directory was on the mounted device which was to be umounted. That doesn't work.

---

### Post by earobinson on 2005-10-31
lol wow stupid mistake, and to think I have rebooted before to fix this. Feeling very stupid right now. I wish umount would give a better message but I guess its kinda hard since it only knows that the device is being used.

Thanks again. Real stupid question im sorry. *blush*

---

### Post by xmastree on 2005-10-31
[QUOTE=earobinson]Thanks again. Real stupid question im sorry. *blush*[/QUOTE]Relax, we've all done it...
Otherwise, how would we learn? :rolleyes:

---

