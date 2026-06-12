---
title: "USB issues"
date: 2006-10-22
forum: General Help
---

### Post by sandpvrr on 2006-10-22
Hello All,
      I've gotten Ubuntu (Dapper Drake) installed on my Father's computer. He is what one would consider to be a VERY casual user. He does not want, need, or wish to understand how the OS works, he just wants it to work, everytime, without problems. Therefore, everytime there is a hitch, I get called. BTW, his previous OS was Windows 98 second edition.
      Here's the situation - when his USB compact flash card reader is plugged in, all the images are viewable, but they cannot be cut off the card, deleted, etc. The permissions tab of the drive looks ok, and I have edited fstab to look: 
```
/dev/sda1       /media/sda1     vfat    rw,suid,dev,exec,auto,user,sync,utf8,umask=007,gid=46 0       1

```
Now if I've read the information on TuxFiles correctly (posted by another poster on another thread) that should enable read, write, execute commands by an ordinary user, and solve the problem. However, it isn't. 
       Any help would be appreciated!
       Thanks!
       cya, Joey

---

### Post by sandpvrr on 2006-10-22
Oh - BTW - automounting seems to be working just fine, as long as the card is in the reader first.
     -Joey

---

### Post by fisherman783 on 2006-11-15
I got my vfat drives to work by adding this option:
```
umask=0000
```
As it was explained to me, 0000 gives permissions to all users.  So, perhaps not the best solution for some people, but it's what I needed.

---

