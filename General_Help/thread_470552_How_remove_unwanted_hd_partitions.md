---
title: "How remove unwanted hd partitions?"
date: 2007-06-11
forum: General Help
---

### Post by dude1234 on 2007-06-11
I bought a spare pc that had windows XP. I installed Ubuntu 6.10. During the installation I wanted to remove ALL prior partitions on the 20 gig hdd. However, I might not have done this. I'm not sure!

How can I check the status of hdd paritions?

How can I fix it so there is only a single partition on the hdd?

Preferably I don't want to re-install the OS unless essential.

---

### Post by total wormage on 2007-06-11
you'll need to install and run gparted

just:
```
sudo apt-get install gparted
```

in a terminal :] and then run it

---

### Post by dude1234 on 2007-06-14
Before I install "gparted", can someone tell me how to check the size of the partition I have now?

I know how to do this in windows - by opening a file explorer window and right click on the c: drive and click on properties. I tried something similar in Ubuntu (i.e. opened the file manager thing which was called a different name) but was unable to figure out what to do next as there was no apparent equivalent of the root directory or c: drive as most call it.

---

### Post by thePsychologist on 2007-06-15
If you install gparted, it will tell you the size of your partition. If you want you can do it without gparted like this:

```
df -h
```

In a terminal. If you're using GNOME go to Accessories> Terminal in the applications menu and type that code and you'll see something like:

> 
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              19G   13G  4.9G  73% /
varrun                221M   88K  221M   1% /var/run
varlock               221M  4.0K  221M   1% /var/lock
udev                  221M  128K  220M   1% /dev
devshm                221M     0  221M   0% /dev/shm
lrm                   221M   19M  202M   9% /lib/modules/2.6.15-27-386/volatile
/dev/hda3             4.6G  1.7G  2.7G  39% /media/feisty


Now the last column is the mount point. The / in the first line, last column indicates that it's where the whole filesystem is. That's what you want. Mine is 19GiB.

---

### Post by dude1234 on 2007-06-25
I did what you said, but it appeared to me that this can only find and re-partition the partitions that ubuntu used when I did the original install.

In my case it appears I have a 16 GB HD but I believe I have a 20 GB and somewhere there is 4 gig that was originally partitioned before I loaded ubuntu and I can't get to it .

Is there a CD or a floppy disk bootable version of linux that I can utilise to investigate the HD remotely?

---

### Post by merlinus on 2007-06-25
Try gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

