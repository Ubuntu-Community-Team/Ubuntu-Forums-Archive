---
title: "Not Enough Disk Space in Boot?"
date: 2016-07-19
forum: General Help
---

### Post by newbuntuser2 on 2016-07-19
Hi halogen, I really need some help here.
I have tried removing my old kernels and still seem to be low on space in /boot.

Running uname -a gives:
```
Linux MyUb 4.2.0-42-generic #49-Ubuntu SMP Tue Jun 28 21:26:26 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
```

```
dpkg-query -W -f '${binary:Package}\n' | grep -P '^linux'Gives:

linux-firmware
linux-generic
linux-headers-4.2.0-42
linux-headers-4.2.0-42-generic
linux-headers-generic
linux-image-4.2.0-42-generic
linux-image-extra-4.2.0-42-generic
linux-image-generic
linux-libc-dev:amd64
linux-sound-base
linux-tools-4.2.0-42
linux-tools-4.2.0-42-generic
linux-tools-common
linux-tools-virtual
```

```
running ls /boot | grep vmlinuz
Gives:
vmlinuz-4.2.0-42-generic
```

```
Running df -h
Gives:
Filesystem      Size  Used Avail Use% Mounted on
udev            3.9G     0  3.9G   0% /dev
tmpfs           790M  9.6M  780M   2% /run
/dev/dm-0       451G  122G  306G  29% /
tmpfs           3.9G   19M  3.9G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda1       236M   88M  137M  40% /boot
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           790M   52K  790M   1% /run/user/1000
```

The Error says I need 165M of space and that I need to free at least 22.1M in /boot.

After removing the last kernel hoping to free that 22.1M it seems to have done nothing. (by last kernel i mean sudo apt-get purge linux-image-3.19.0-15-generic)
I've also done all the autoremove and clean command over and over after restarting and so on. I seem to have hit a wall.

I only have this kernel (4.2.0-42-generic) and no prior backup yet i still dont have enough space for some reason and as far as I've seen for everyone else it seemed to be enough to allow the upgrade to 16.04.

Please help and any assistance would be appreciated.

---

### Post by howefield on 2016-07-19
Post moved to own thread and code tags added.

---

### Post by yancek on 2016-07-19
What exactly are you trying to do when you get this "error"?  Is this an upgrade to 16.04?  You have 137MB of free space in your boot partition and over 300GB on the / partition which should be more than enough.  Post the exact error.

---

### Post by newbuntuser2 on 2016-07-20
Thanks you for moving this to a new post and adding tags, I wasnt sure if i should.

Yes this is for an upgrade from 15.10 to 16.04LTS
Sure here is the exact error I get:
[ATTACH=CONFIG]270229[/ATTACH]
In case that doesn't work for some reason, it says:

"The upgrade has aborted. The upgrade needs a total of 165 M free space on disk '/boot'. Please free an additional 22.1 M on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

So what I have done so far, first was try the sudo apt-get clean and it did nothing ofcourse. Then I searched it and eventually found that most people just needed to clean out the old kernels. Which i then did and am now left with only this kernel and so on as previously mentioned. 
What else could I do to make more free space in /boot or how could I possibly increase the size of this directory?

---

### Post by newbuntuser2 on 2016-07-20
Or a better question is how can I make my upgrade to 16.04 work?

---

