---
title: "mounting encrypted external drive"
date: 2007-12-08
forum: General Help
---

### Post by m.musashi on 2007-12-08
I used this how to a while back to create an encrypted external hard drive.

[http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/](http://ubuntu-tutorials.com/2007/08/17/7-steps-to-an-encrypted-partition-local-or-removable-disk/)

Everything worked fine and I have been using the drive for a while. When I did a clean install of Gutsy the drive is no longer accessible. That makes sense so I followed the steps again skipping the ones that would make or format the drive as I don't want to do that.

I did the following steps:
```
sudo aptitude install cryptsetup
sudo modprobe dm-crypt
sudo cryptsetup luksOpen /dev/sde2 data
```

When I plug the drive in it pops up a password window. I enter the password and then nothing happens.

Any idea what I'm missing?

Thanks.

---

### Post by m.musashi on 2007-12-09
Okay, I kind of figured this out. If i use
```
sudo cryptsetup luksOpen /dev/sde2 data
sudo mount /dev/mapper/data /media/data
```
It will mount. However, it doesn't do it automatically as it used to. Also, the first time I tried it, I had to use the long crypto file name of the partition that was listed in /dev/mapper/ but now it seems to show as the short name "data".

Any ideas how to get this to mount automatically once again? Thanks.

---

### Post by mknudsen on 2007-12-10
I think I have a similar problem. I have two external luks-encrypted disks, one of them won't mount automatically. There is no Problem in mounting it manually and it seems to be encrypted correctly (since there is a shortcut in /dev/mapper/luks_blabla which I can mount).

Anyone got any Ideas?

---

### Post by dimeotane on 2007-12-15
Automounting a LUKS encrypted drive used to work flawlessly in older versions of Ubuntu, but in gutsy it appears to fail mounting after you enter the passphrase. 

[https://launchpad.net/ubuntu/+source/udev/+bug/78848](https://launchpad.net/ubuntu/+source/udev/+bug/78848)

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/156285](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/156285)

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/117011](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/117011)

[https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/148003](https://bugs.launchpad.net/ubuntu/+source/gnome-mount/+bug/148003)


Any solutions anyone?

---

### Post by m.musashi on 2007-12-16
Well, good to know it's not just a PEBKAC problem :).

---

