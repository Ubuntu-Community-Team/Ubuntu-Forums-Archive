---
title: "missing harddrive space puzzle"
date: 2007-12-14
forum: General Help
---

### Post by capitol on 2007-12-14
Hi all

I think i have some files on my harddrive that i doesn't seem to be able to reclaim the space for and i can't find them:

root@vito:/# du -h --max-depth=1 -x
4.0K    ./initrd
4.0K    ./srv
16K     ./lost+found
16K     ./media
6.4G    ./home
18M     ./boot
1.7G    ./root
10G     ./var
7.6M    ./sbin
11M     ./etc
136M    ./lib
0       ./proc
4.0K    ./mnt
1.1G    ./usr
4.0K    ./opt
5.7M    ./bin
0       ./sys
0       ./dev
9.7M    ./tmp
20G     .

root@vito:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              65G   50G   12G  82% /
varrun                2.0G   88K  2.0G   1% /var/run
varlock               2.0G     0  2.0G   0% /var/lock
udev                  2.0G   60K  2.0G   1% /dev
devshm                2.0G     0  2.0G   0% /dev/shm
/dev/sdb1              68G   45G   20G  70% /media/sdb1
tmpfs                 2.0G   38M  1.9G   2% /lib/modules/2.6.22-14-generic/volatile


as we can see i have about 30G on my / partition that i can't find, does anyoen have any idee on how to resolve this.

---

### Post by HermanAB on 2007-12-14
Hmm, I guess that you are using Ext3.  Try disabling and re-enabling the journal. 

I use JFS since it doesn't have this problem.

---

### Post by psusi on 2007-12-14
Try booting from the livecd and doing a fsck -f /dev/sda1

---

### Post by capitol on 2007-12-20
Thanks for the tips.

I found the error, it was that the /etc/init.d/apache2 script didn't kill the apache process as it should.

That way the apache processes still lived, and held the log files open, but the logfiles had already been deleted by the log rotate scripts, so they wasn't visible for du, but the space still hadn't been reclaimed for general use.

So i guess that you would have the same problem with JFS ;)

---

