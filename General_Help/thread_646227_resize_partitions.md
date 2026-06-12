---
title: "resize partitions"
date: 2007-12-20
forum: General Help
---

### Post by geoffDeGeoffGeoff on 2007-12-20
I have root ssh only access to a server running ubuntu 6.06.  I am trying to install zimbra on it, but zimbra needs all the space in /opt.  df -h on the server gives me:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             4.6G  910M  3.5G  21% /
varrun                1.5G   64K  1.5G   1% /var/run
varlock               1.5G  4.0K  1.5G   1% /var/lock
udev                  1.5G  124K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
/dev/sda8             449G  129M  426G   1% /home
/dev/sda7             4.6G  349M  4.1G   8% /var

I would like to increase the size of / and shrink /home.  How would I go about this?

I took a look at parted but didn't really understand the steps I should follow.

Is this something simple or should I bite the bullet and pay the server hosting company to reinstall with the disc setup how I specify?

---

### Post by xadder on 2007-12-21
I did something similar a while ago. I used gparted to shrink my / so that /home could be bigger. There weren't any problems at all, even though I had never tried such a thing and assumed it would all go wrong. (I had a good backup though, so could have re-installed from scratch if needed).

If I remember right, it is just to do things in the right order. Make the bigger patrition smaller, then expand the remaining one into the space which is left. It was all pretty intuitive.

Still, remember that backup!

---

### Post by bingoUV on 2007-12-21
Output of the following will be more informative to people trying to help you.
```

sudo /sbin/fdisk -l

```

But, prima facie, it seems that you will have to first shrink sda8, then move it down, then move down sda7 and then expand sda6.

---

