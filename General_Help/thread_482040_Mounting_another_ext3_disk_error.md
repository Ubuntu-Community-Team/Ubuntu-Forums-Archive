---
title: "Mounting another ext3 disk error"
date: 2007-06-23
forum: General Help
---

### Post by juantovarm on 2007-06-23
Hi! I have one small problem. I have two hard drives, a 160 giga and a 10 giga. On the 160 i have ubuntu, on the other fedora 6. The 10 is for learning purposes only. I resolved dual boot, now i can do it, no problem. What i oild like to do now is to access y fedora in my ubuntu

I was able to mount the /boot of fedora, i have access to it in ubuntu but ONLY the boot nothing else. When i try to mount the rest i get an error that says:   

wrong fs type, bad option, bad superblock on /dev/sdb2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Any ideas????????????':-k:-k

Thanks

---

### Post by mustali on 2007-06-23
Are you able to boot Fedora fine? Did you cleanly shutdown Fedora before booting into Ubuntu?

Filesystem check may uncover problems.  Try the following to find bad blocks on your filesystem (assuming you have ext3 type. for ext2, use fsck.ext2). 
```

fsck.ext3 -cv of /dev/sdb2

```

-p option would automatically fix the bad blocks but I suggest you do a check first. more info on man fsck.ext3

HTH

---

### Post by mustali on 2007-06-23
typo in the command mentioned above. Should read

```

fsck.ext3 -cv /dev/sdb2

```

---

### Post by juantovarm on 2007-06-23
Thanks for the reply Mustali, 
I can boot into fedora perfectly, i have no problems with that

I ran your command and this was the output:
juan@juan-desktop:~$ sudo fsck.ext3 -cv /dev/sdb2

e2fsck 1.40-WIP (14-Nov-2006)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdb2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I cleanly shutdown fedora, it has given me no problems but this one

---

### Post by mustali on 2007-06-23
I looked around google and found a lot of other people having had similar experiences. This post ([http://www.computing.net/linux/wwwboard/forum/28506.html](http://www.computing.net/linux/wwwboard/forum/28506.html)) shows how using a different superblock size helped fix the partition. so give -b option a try with sizes 8193 and 32768.

However, it is wierd that the problem seems to related to the partition but Fedora is robust enough to work around it.

HTH

---

