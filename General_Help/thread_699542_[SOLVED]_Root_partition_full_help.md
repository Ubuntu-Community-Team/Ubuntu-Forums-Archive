---
title: "[SOLVED] Root partition full help"
date: 2008-02-17
forum: General Help
---

### Post by drfox on 2008-02-17
I was getting a disk full error on my / partition, which is sda2. I have /boot, /home, /opt, and /swap on other partitions.
My / was 10GB. I booted to live disk, ran gparted, and shrank home to 200GB and expanded / to 20GB.
After rebooting, gparted looks as though I have a 20GB partition which is nearly 100% full. 
But df -h gives me this:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.7G  9.2G  5.4M 100% /
varrun               1007M  240K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  136K 1007M   1% /dev
devshm               1007M  8.0K 1007M   1% /dev/shm
lrm                  1007M   38M  970M   4% /lib/modules/2.6.22-14-generic/volatile
/dev/sda1             3.9G   90M  3.6G   3% /boot
/dev/sda3             198G   22G  172G  12% /home
/dev/sdb1             193G  188M  183G   1% /media/sdb1
/dev/sdb2             170G  188M  163G   1% /media/sdb2
/dev/sdb3             9.7G  2.4G  6.8G  26% /media/sdb3
/dev/sdb6              83G   42G   38G  53% /media/sdb6
/dev/sda6             4.6G  289M  4.1G   7% /opt

Obviously, df -h thinks I still have a 10GB root. How can I fix whatever needs to be fixed?

Thanks. Larry

---

### Post by astrotech226 on 2008-02-17
You've increased the size of the partition, but not the size of the filesystem.  Assuming you are using ext3, look into the "resize2fs" man pages.

---

### Post by drfox on 2008-02-17
> **astrotech226 said:**
> You've increased the size of the partition, but not the size of the filesystem.  Assuming you are using ext3, look into the "resize2fs" man pages.

Perfect. I ran the utility and it worked! Thank you!

Larry

---

