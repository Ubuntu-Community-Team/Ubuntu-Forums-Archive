---
title: "Something filling my harddisc rapidly"
date: 2013-08-03
forum: General Help
---

### Post by ihsankocak on 2013-08-03
I should have space but really  dont have space:
```
Filesystem         1K-blocks      Used Available Use% Mounted on
/dev/sda6          302247360 302247360         0 100% /
none                       4         0         4   0% /sys/fs/cgroup
udev                 4005096         4   4005092   1% /dev
tmpfs                 804408      1732    802676   1% /run
none                    5120         0      5120   0% /run/lock
none                 4022040        12   4022028   1% /run/shm
none                  102400         8    102392   1% /run/user
/dev/sda1             507904     51464    456440  11% /boot/efi
/home/abc/.Private 302247360 302247360         0 100% /home/abc
/dev/sdb1          302247360 302247360         0 100% /media
```

Something is filling my hard disc.Today i made a mistake changed the ownership of /usr.Then i could not use startx after this change.So used sudo startx.But the system did not see my external hard disc.I tr&#305;ed to mount it with mount with
```
sudo mount -t ntfs /dev/sdb1 /media
```

When it gives the no space error, i tried to unmount this but it says: "media not mounted". I do not know if all these are related with no space issue but maybe there is relation.So what should i do to stop the hard disc filling action?

---

### Post by phillw on 2013-08-03
/usr should be owned by root. I'm guessing that you are getting many error messages logged under /var/log. Try issuing:
```

du -h /var/log

```
to see if this is the case. If so, then you need to stop the error messages (resetting the ownership should do that) and then delete the error log files.

---

### Post by ihsankocak on 2013-08-03
Thank you for the reply.You are right there is an 265 G log there.Actually i changed ownership to root but it should be from old days.Thank you very much again.
Edit: I am new to this community.So how can I select as right answer your answer?

---

### Post by ihsankocak on 2013-08-03
I am so sorry.After restarting the system it shows the emptyness.So you are right.The porblem was log file.

---

### Post by phillw on 2013-08-03
the mount option will not change the file type, you let mount 'know' to try a filesystem of type ntfs. If it is not file system of type ntfs, mount will fail. [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount) covers the mount command in more detail. I'm puzzled, as you have said you have deleted the 256Gb log file? Please re-check that it is indeed deleted. You may need to use sudo to delete a system log file.

---

### Post by ihsankocak on 2013-08-03
I am so sorry.After restarting the system it shows the emptyness.So you are right.The porblem was log file.

---

### Post by phillw on 2013-08-03
Great to hear! please use the 'thread tools' drop down to mark this as [solved]. :D

---

