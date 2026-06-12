---
title: "Fake or Ghost Audio CD Icon"
date: 2007-06-06
forum: General Help
---

### Post by ddumanis on 2007-06-06
Hi,

Ever since the new kernel update, I've been seeing an "Audio Disc" on my desktop even though there's no CD in the drive. Double-clicking it reveals ghost tracks in Sound Juicer with some VERY odd times, including negative minutes!

Any solution to make this thing go away? I've tried editing fstab--there's nothing in there but ext1 and ext3 hard drive partitions now, but I'm still having the same problem.

---

### Post by gerscht on 2007-06-06
what does your mtab say?
```

sudo less /etc/mtab

```
Is there anything which points to this 'CD'?

---

### Post by ddumanis on 2007-06-06
Not that I can tell:

```



/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.20-16-generic/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/etc/mtab (END) 


```

---

### Post by gerscht on 2007-06-06
You're right, there doesn't seem to be anything.
Another place to look is 
```

sudo less /media/.hal-mtab
```
This is where hot plugged devices go into (and CDs/DVDs)

---

### Post by wribeiro on 2007-11-26
I have the same issue here.
I have a Medion Life Notebook, AMD Athlon 1.8 MHz, 512MB RAM, CD/DVD RW, ATI Radeon 1280x800, Ubuntu 7.10
The first time I installed Ubuntu 7.1 on the same computer, a few weeks ago, it didnt happen.
Now, some minutes after login, appears a "ghost" Audio CD Icon on my desktop and a Error Message from Sound Juicer: "can not read track list" "track numbers must be within 1..99"
But the cd drive is empty!!
After this, I can't eject the drive anymore.
I found another post about the same problem:
[http://ubuntuforums.org/showthread.php?p=3842228#post3842228](http://ubuntuforums.org/showthread.php?p=3842228#post3842228)
Thank you.

---

