---
title: "So I have over 1TB on a 6GB ramdisk"
date: 2013-06-05
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-06-05
I have 12GB ram (3 stick of 4gb)
for the sake of science how is this possible
```
$ cat /etc/fstab | grep '/tmp'
# /tmp was moved to RAM after installation
tmpfs                                     /tmp            tmpfs   defaults,noatime,mode=1777 0       0
$ ls -l /tmp
total 6152936
-rw-rw-r-- 1 chad chad            0 Jun  5 16:14 canvas.gif
drwxr-x--T 2 chad chad           40 Jun  5 16:02 chad-Desktop
-rw------- 1 chad chad 687194767360 Jun  5 16:56 magick-0JMt1Qud
-rw------- 1 chad chad 549755813888 Jun  5 16:14 magick-IknG9i1h
drwx------ 2 chad chad           40 Dec 31  1969 orbit-chad
drwx------ 2 root root           40 Jun  5 16:02 pulse-PKdhtXMmr18n
drwx------ 2 chad chad           60 Jun  5 16:02 ssh-GnQzoOrlU7le
-rw------- 1 chad chad            0 Jun  5 16:02 tmp1rvyRb
ls -s /tmp
total 6152936
      0 canvas.gif       6152932 magick-IknG9i1h           0 ssh-GnQzoOrlU7le
      0 chad-Desktop           0 orbit-chad                0 tmp1rvyRb
      4 magick-0JMt1Qud        0 pulse-PKdhtXMmr18n

```

---

### Post by sanderj on 2013-06-05
Cool! And what's the output of "mount" and "mount | grep tmp"?

---

