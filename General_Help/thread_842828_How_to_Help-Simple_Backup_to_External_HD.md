---
title: "How to Help-Simple Backup to External HD"
date: 2008-06-27
forum: General Help
---

### Post by Daddyo-613 on 2008-06-27
My system:
```
:~$ cat /proc/version
Linux version 2.6.24-19-generic (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:43:41 UTC 2008

```

My External HD: Western Digitial 500 GB USB hard drive.

I have been searching the forum for a "How-to" to backup the contents of my internal HD to an external HD but I must be using the wrong search string. 

I have a stand alone PC. I am not operating a server. Because my external HD is larger than my internal drive, I would like to copy my internal HD onto the external HD as a backup that I can use to restore my system and my files in the event of a catastrophic failure of my HD or because I managed to royally screw up my system (again) by playing with it.

I looked at "dd --help" there seem to be a lot of options to limit what is being copied to conserve space but that's not an issue for me right now.

I expect that there is a simple command sequence I can use but I can't find it. Help would be appreciated.

---

### Post by russlar on 2008-06-27
tar is your friend. there are how to's floating around here.b

---

### Post by Daddyo-613 on 2008-06-27
> **russlar said:**
> tar is your friend. there are how to's floating around here.b

I'm not sure I follow your line of thought. Are you suggesting that I create a tar of my existing HD?

---

### Post by Zardus on 2008-06-27
First you'd need to determine which partition you're running Linux from. One way to do that is to run (from the terminal):

```
# sudo df
```

Here's some example output from one of my machines:

```
# sudo df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              8151384   7043488    693824  92% /
/dev/sda1               101089     15088     80782  16% /boot
/dev/sdc1             20635700   6573884  14061816  32% /mnt/data
varrun                 1553404       332   1553072   1% /var/run
varlock                1553404         0   1553404   0% /var/lock
udev                   1553404        48   1553356   1% /dev
devshm                 1553404         0   1553404   0% /dev/shm
tmpfs                  1553404     38176   1515228   3% /lib/modules/2.6.24-19-generic/volatile
```

The /dev/sd* (or if you are running IDE drives, /dev/hd*) partitions are the ones you're going to want to back up. The others you can ignore.

The next step would be to get those filesystems mounted read-only so nothing's changing while you're backing up. You can probably do that by booting the Ubuntu livecd (I don't think it automounts your partitions. It if does, unmount them). Then plug in a really big drive and Ubuntu should mount it somewhere under /media (when I plug in my My Book, it gets automatically mounted at "/media/My Book"). What you would then do (from the terminal), with the above partition setup, is:

```
# sudo dd if=/dev/sda1 of="/media/My Book/sda1.image" bs=1024
# sudo dd if=/dev/sda2 of="/media/My Book/sda2.image" bs=1024
# sudo dd if=/dev/sdc1 of="/media/My Book/sdc1.image" bs=1024
```

You can then test these backups by doing:

```
# sudo mkdir -p /mnt/backup_test
# sudo mount -o loop,ro "/media/My Book/sda1.image" /mnt/backup_test
(at this point you can navigate to /mnt/backup_test and make sure everything's there)
# sudo umount /mnt/backup_test
```

To restore these partitions, you would boot off the livecd, put in your big drive, and do:

```
# sudo dd of=/dev/sda1 if="/media/My Book/sda1.image" bs=1024
# sudo dd of=/dev/sda2 if="/media/My Book/sda2.image" bs=1024
# sudo dd of=/dev/sdc1 if="/media/My Book/sdc1.image" bs=1024
```

Note the switched 'of' (output file) and 'if' (input file). This will overwrite the current data on your drive, so be careful!

Also note that all this is off the top of my head so if any of this stuff errors out you should not ignore the error. This is dangerous stuff here.

Lastly, **there are better ways to do this**. Check out partimage; you can install it through the package manager. It looks like it will create smaller backups by not backing up unallocated space, too. There's probably plenty of other stuff out there like that as well.

Good luck!

---

### Post by Zardus on 2008-06-27
BTW, obviously my instructions above have nothing to do with tar. Didn't mean to cut into your method, russlar. When I started typing there weren't any replies yet :-)

Anyways, it looks like everything I wrote was pretty redundant. Check out [https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by beren.olvar on 2008-06-27
I use flyback [http://code.google.com/p/flyback/](http://code.google.com/p/flyback/)

its simple and allows me to restore previous versions...
hope you like it too

cheers

---

