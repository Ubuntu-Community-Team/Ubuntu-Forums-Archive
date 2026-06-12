---
title: "[SOLVED] Vanishing space when copying between two machines"
date: 2008-07-01
forum: General Help
---

### Post by gawron on 2008-07-01
I just upgraded my notebook (from Lenovo/IBM T42 to T61) and I am moving my files over to a new machine (via ssh, over network). I just noticed that files, that occupied around 6.5 GB on a 10GB partition (ext3 filesystem) on old notebook, take now 9.5GB on a 11GB partition (also ext3) on a new notebook - as reported by df! These two partitions are both ext3, with standard mkfs options (4KB cluster size etc.). The only difference (that I can think of...) except slightly different partition sizes is that on old machine the partition was /dev/sda3 while on the new one it is /dev/sda4 (the HDD is 120GB on both machines). What the...??? Any ideas where to start looking? :-)

---

### Post by soccerboy on 2008-07-01
how are you checking space usage.  The disk usage analyzer reports double the amount because of the gnome-vfs compatible mount in your home directory.  It basically scans your hd twice.

---

### Post by gawron on 2008-07-01
I check with df in shell. Here's the output.

On new machine:

```

root@gawron-laptop:~# df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              6.0G   3.0G   2.7G  53% /
varrun                 517M   107k   517M   1% /var/run
varlock                517M      0   517M   0% /var/lock
udev                   517M    58k   517M   1% /dev
devshm                 517M    13k   517M   1% /dev/shm
lrm                    517M    40M   478M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              101G    43G    53G  46% /home
/dev/sda4               11G   9.4G   562M  95% /zebra

```

and on old machine:
```

gawron@gawron-laptop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               10G   3.7G   5.8G  39% /
varrun                 530M   259k   530M   1% /var/run
varlock                530M      0   530M   0% /var/lock
udev                   530M    66k   530M   1% /dev
devshm                 530M   373k   530M   1% /dev/shm
lrm                    530M    40M   491M   8% /lib/modules/2.6.24-19-generic/volatile
/dev/sda4               97G    92G   547M 100% /home
/dev/sda3              9.9G   6.5G   2.9G  70% /zebra
gvfs-fuse-daemon        10G   3.7G   5.8G  39% /home/gawron/.gvfs

```

the partition in question is mounted as /zebra, it contains one Thunderbird profile... BTW, all this on Hardy

---

### Post by gawron on 2008-07-02
OK, I figured it out, so just in case someone else stumbles upon this. Apparently Thunderbird uses quite a lot of sparse files, and standard copy writes them on destination as normal files. To check one should test directory size with du command with and without --apparent-size argument - if there is a lot of sparse files, the outputs will be different.

I finally copied the directory using rsync with -S option ("efficiently treat sparse files").

---

