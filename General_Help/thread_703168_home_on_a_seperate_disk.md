---
title: "/home on a seperate disk?"
date: 2008-02-21
forum: General Help
---

### Post by iancvt55 on 2008-02-21
Hi

Is it possible to move or recreate my /home onto a seperate disk not minimise the risks should i loose my Ubuntu disk?

thanks

Ian

---

### Post by njparton on 2008-02-21
It should be possible.

Create a suitable partition on the new disk, mount it as something else (e.g. /mnt/temp) copy you existing home files to it, then edit your /etc/fstab file to mount the new drive as your /home partition during next reboot.  Then reboot.

Don't delete your old /home partition until you're 100% sure that it works.

Use gparted for creating and formatting the new partition.

---

### Post by Carl H on 2008-02-21
He doesn't need to repartition; he says he's going to use a seperate disk.  But the new disk will need to be formatted, which can be done with GPartEd. 

Remember to either do the copying of /home from the command line, or make sure that you have "Show Hidden Files" set if you're doing it from the file manager.

---

### Post by bodhi.zazen on 2008-02-21
Careful, a simple copy will not work.

Follow a guide : [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)

---

### Post by phrawzty on 2008-02-21
> **Carl H said:**
> Remember to either do the copying of /home from the command line, or make sure that you have "Show Hidden Files" set if you're doing it from the file manager.

One of more reliable ways to ensure that the files are copied *exactly* would be to use [Rsync]("http://rsync.samba.org") via the shell.  Something like this would to the trick :
```
$ sudo rsync -aHA /home /mnt/newhome
```

Optionally, adding switches would produce some nice output :
```
--progress -h --stats
```

---

### Post by njparton on 2008-02-21
> **Carl H said:**
> He doesn't need to repartition; he says he's going to use a seperate disk.  But the new disk will need to be formatted, which can be done with GPartEd. 

Remember to either do the copying of /home from the command line, or make sure that you have "Show Hidden Files" set if you're doing it from the file manager.

Depends on if he wants to use the whole disk or not?

---

### Post by L8erG8er on 2008-02-21
I moved my /home to a completely different hard drive, using an excellent tutorial found here:  [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

