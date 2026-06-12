---
title: "Use SSD cache drive: is this possible?"
date: 2018-02-25
forum: General Help
---

### Post by ubname on 2018-02-25
I have a laptop with a "little" (20 Gb) SSD drive that is suppose to be used as cache to speed up the regular spinning HD, is it possible to activate such a function in Ubuntu? Thanks.

---

### Post by HermanAB on 2018-02-25
Bcache:
[https://wiki.archlinux.org/index.php/Bcache](https://wiki.archlinux.org/index.php/Bcache)

---

### Post by ubname on 2018-02-25
Thanks Herman, I understand it's not worth the hassle, would it make sense to install with only /boot on ssd and / on the hdd? (20 Gb too small for / IMO).

---

### Post by HermanAB on 2018-02-25
Well, why do you boot all the time?  Use suspend.  That will fix the boot time issue and the system will be ready immediately when you open the lid.  A laptop PC never needs to reboot.  My laptops run for multiple months without rebooting.  Usually I only need to reboot after something screwed up with the display when unplugging a projector in a conference room.

Secondly, 20 GB cache is plenty as a cache for a Linux system that is only 2 GB or so in size.

---

### Post by ubname on 2018-02-25
Actually I do not have any boot time issue, I'm now using the SSD as root / and the HD as home but it's too small for root, the logical use would be as cache indeed as you say but i understand that it's not so simple by the link you sugget, have you tried?

---

### Post by oldfred on 2018-02-25
I have seen others install / to SSD, if primarily Ubuntu users.
I normally use 25 to 30GB for /.

My main working install is 16.04 and is now up to 12GB used. 
New install without much history built up uses less than 6GB.

```
fred@Z170N:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            7.8G     0  7.8G   0% /dev
tmpfs           1.6G  9.7M  1.6G   1% /run
/dev/sda2        30G   [COLOR=#ff0000]12G[/COLOR]   17G  41% /
tmpfs           7.8G  200M  7.6G   3% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
tmpfs           7.8G  8.0K  7.8G   1% /tmp
/dev/sda1        50G   54M   50G   1% /boot/efi
/dev/sdb6       202G   49G  143G  26% /mnt/data
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           1.6G   48K  1.6G   1% /run/user/1000
/dev/sdc2        21G  [COLOR=#ff0000]5.6G[/COLOR]   14G  30% /media/fred/xenial64
/dev/sdc3        36G   27G  8.1G  77% /media/fred/data64
/dev/sdb2        30G  [COLOR=#ff0000]5.0G [/COLOR]  24G  18% /media/fred/zesty
/dev/sda4        25G  [COLOR=#ff0000]5.7G[/COLOR]   18G  24% /media/fred/bionic
```

---

### Post by HermanAB on 2018-02-25
Cache use is much smaller than the total size of /.  This is simply because you never run all programs at the same time and lots of them, you will never use and never figure out what on earth they are for.

Installing bcache is painful and not for the faint hearted: [http://www.kloppenborg.net/blog/2016/02/17/installing-ubuntu-1510-with-bcache-support](http://www.kloppenborg.net/blog/2016/02/17/installing-ubuntu-1510-with-bcache-support)

However, Linux uses RAM for disk cache (called disk buffers) automatically.  So you can avoid all the above head-ache by simply installing more RAM in your machine.

---

### Post by ubname on 2018-02-25
I'm on 17.10 and just discovered that i'n hit with this bug:

[https://bugs.launchpad.net/ubuntu/+source/snapd-glib/+bug/1723362](https://bugs.launchpad.net/ubuntu/+source/snapd-glib/+bug/1723362)

I would try the link from Herman with 18.04 but is the above bug fixed in 18.04?

thanks!

---

