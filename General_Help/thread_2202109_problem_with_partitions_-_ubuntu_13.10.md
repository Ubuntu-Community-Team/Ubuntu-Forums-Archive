---
title: "problem with partitions - ubuntu 13.10"
date: 2014-01-27
forum: General Help
---

### Post by jsabina1 on 2014-01-27
Hi everybody,
I have problems with my partitions..
When I installed ubuntu there was already windows 7 installed and I didn't use all the space.
So I though later to shrink the space on windows 7 and create a new partition.
That's ok and it works, but to make it work I have everytime to click it and insert the password even if I put the permission to 777.

Just to give you an example, I called it data and I put the virtual disk for virtual box. It would not work until from the gui I tried to access the disk data and insert the password.

I also added a swap partition on that one and it's not active.

df -h
/dev/sda5                 130G   21G  103G  17% /
none                      4.0K     0  4.0K   0% /sys/fs/cgroup
udev                      3.9G  8.0K  3.9G   1% /dev
tmpfs                     785M  1.2M  784M   1% /run
none                      5.0M     0  5.0M   0% /run/lock
none                      3.9G  608K  3.9G   1% /run/shm
none                      100M  8.0K  100M   1% /run/user
/home/atin/.Private  130G   21G  103G  17% /home/atin
/dev/sda4                  91G  7.2G   79G   9% /media/atin/data

---

### Post by Bashing-om on 2014-01-27
jsabina1; Hi !

In order for the partitions to be mounted at boot, entries must be made into the file "/etc/fstab " (File System TABle).
You certainly want the swap partition to mount at boot, maybe not so with a "data" partition (?).
I myself prefer to mount my "data" partitions as on-demand to help preclude chance alterations to my precious preserved data.
But, it is your system, we will advise you as your request.


Show us what we are working with:
Post the out put of terminal codes - BeTween Code Tags - :
```

sudo fdisk -lu
sudo blkid
cat /etc/fstab

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And hey ->
[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

