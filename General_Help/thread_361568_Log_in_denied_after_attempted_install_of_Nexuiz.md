---
title: "Log in denied after attempted install of Nexuiz"
date: 2007-02-14
forum: General Help
---

### Post by forpeterssake on 2007-02-14
I attempted to install Nexuiz but part of the installation failed. When I tried to play the game, the screen essentially froze up with big blocks of pixels.

When I restarted, I could no longer log in. I got a message almost immediately that said I had been kicked out earlier than 10 seconds, and there may be an installation problem or I have run out of disk space. It recommends using a failsafe session to correct the problem, but I'm not sure how to fix it. I'm not even know if Nexuiz is the cause of the problem.

---

### Post by taurus on 2007-02-14
Boot into recovery mode from GRUB menu and post the output of this command here.

```
df -h
```

---

### Post by forpeterssake on 2007-02-14
Here's the output I get after booting in recovery mode. It's all jumbled together, but hopefully it makes sense.
> File System    Size    Usd     Avail  Use     Mounted on
/dev/hda3      2.5G   2.4G    0       100%  /
varrun           236M   16K    236M   1%    /var/run
varlock          236M     0      236M   0%    /var/lock
procbususb     10M     112K  9.9M    2%   /proc/bus/usb
udev              10M     112K  9.9M    2%   /dev
devshm         236M      0      236M   0%   /dev/shm
lrm                236M    18M   219M    8%  /lib/modules/2.6.17-11-generic/volatile
/dev/hda4      16G     211M   15G     2%  /home
/dev/hda1       57G    4.6G    52G     9%  /media/hda1

The error I apparently get when I try to log in is:
> mkdtemp: private socket dir: No space left on device

If I can't solve the problem, I can always reinstall, but I don't want to lose my data. Is there some way to get it off if I need to reinstall?

---

### Post by GrumpyBob on 2007-02-14
Is the error one about your last session lasting less than 10 seconds?  If so, it's probably the .ICEauthority issue (search the forum for more).
This is easily sorted by logging in failsafe mode, and renaming .ICEauthority as .ICEauthority.bak (or by deleting the file).  Don't forget the leading dot in the filename - it's a hidden file.

Robert

---

### Post by aidanr on 2007-02-14
> **forpeterssake said:**
> File System Size Usd Avail Use Mounted on
/dev/hda3 2.5G 2.4G 0 **100% /**

theres your problem, free up some space from the terminal by deleting anything unneccessary (don't go mad) or enlarge the partiton with gparted

---

### Post by taurus on 2007-02-14
While still in the recovery mode, run

```
aptitude clean
rm ~/.Trash/*
rm /home/**username**/.Trash/*
df -h
```
Replace the **username** with your actual log in name.

---

### Post by forpeterssake on 2007-02-14
Thanks, everyone. I did as Taurus suggested and it freed up 15%, enough to restart. I just reinstalled over the weekend, and I just realized that I installed ubuntu on the wrong partition. I guess Nexuiz was big enough to push me over the edge.

---

