---
title: "swap &quot;not available&quot; causing system freeze 14.04"
date: 2014-05-26
forum: General Help
---

### Post by bnhrobotics on 2014-05-26
I've recently installed Ubuntu 14.04 on a couple of computers. My laptop, in particular, keeps freezing and I've come to realize that it is because I have no swap and I'm running out of ram (only 4GB).  The system monitor says "Swap: not available". I have an encrypted home and let the ubuntu installer pick partition sizes. The disks utility shows 4.2 GB of swap/extended partition which overlap. I'm not sure what the overlapping bit means. The main partition is sda1, extended is sda2 and swap is sda3.

fstab looks like
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID= :) /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID= :) none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

I find it interesting that the swap UUID is commented out. I uncommented it, and rebooted, but nothing changed.

Any ideas how to fix this? Thanks!

---

### Post by LastDino on 2014-05-26
Pardon me, but doesn't that fstab also say that it is encrypted?

---

### Post by bnhrobotics on 2014-05-26
Hi LastDino,

Thanks for your response. I believe you're right, but I've never dealt with encrypted swap systems before, so I'm at a loss.

---

### Post by LastDino on 2014-05-26
I've never worked with encrypted SWAP so this is first for me, lets try.

Does SWAP get mounted for that season when you run following?

```
swapon /dev/sda3
```

Copy paste here if you get any errors regarding that. Technically speaking, it should ask you pass-phrase or something since it is encrypted, but that's just me and I could be wrong.

---

### Post by bnhrobotics on 2014-05-26
```

:):~$ swapon /dev/sda3
swapon: /dev/sda3: stat failed: No such file or directory
:):~$ ls /dev/ | grep sda
sda
sda1
sda2
sda5
:):~$ sudo swapon /dev/sda2
swapon: /dev/sda2: read swap header failed: Invalid argument

```

/dev/sda5 doesn't work either

---

### Post by bnhrobotics on 2014-05-26
So I followed the thread at [http://ubuntuforums.org/showthread.php?t=2084884](http://ubuntuforums.org/showthread.php?t=2084884)

doing 
```

sudo swapoff -a
sudo mkswap /dev/sda5
sudo swapon /dev/sda5
sudo ecryptfs-setup-swap

```

which works! but does not persist after reboot.

---

### Post by LastDino on 2014-05-27
If it is generating UUID for sudo blkid now, then you could simply modify Fstab with it and it should be detected on reboot, again, I can not assure you this as you're using encrypted SWAP.

What I would do now, is check if swapon /dev/sda3 works or not first, if it does, then I would get UUID (if it is showing for you) and edit fstab to detect it on reboot automatically.  

Can you show me out put of 
```
sudo blkid
```
?

---

### Post by Alley_Oop on 2014-05-27
I found a solution which I posted in this thread [http://ubuntuforums.org/showthread.php?t=2224129&p=13027409#post13027409](http://ubuntuforums.org/showthread.php?t=2224129&p=13027409#post13027409)

---

