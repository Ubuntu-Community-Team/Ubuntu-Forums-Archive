---
title: "Disk Full Error"
date: 2008-05-18
forum: General Help
---

### Post by kiwited on 2008-05-18
Since an upgrade this morning I have had a range of problems.

1. I cannot access my email. I get and error message saying there is not enough disk space to download messages.
2. I cannot log out. The little green man disappears when I click on it. Panels top and bottom disappear at the same time.
3. Firefox seemed to lose it's history. The back arrow was greyed out. While I could move forward through links, I was unable to move back.
4. Google Earth no longer works. It doesn't even start the initialisation window.

I have Hardy on a 140gig partition, with an earlier failed hardy install on another partition and Xandros on a third. There is a fat partition for transferring data that has no OS as a fourth. My files take around thirty gig of the 140, but a search of properties for the filesystem shows the disk is full. A search folder by folder seems to have revealed that the media folder is to blame, as it seems to have added all the other partitions volumes to become too large for the partition that it is on. I have tried umounting the other disks, but to no avail.

Any ideas??

Theo

---

### Post by chrisccoulson on 2008-05-18
Could you post the output of
```
df -h

```
Thanks

---

### Post by kiwited on 2008-05-18
Thanks for the reply.

The output reads:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             105G  100G     0 100% /
varrun               1007M  224K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   52K 1007M   1% /dev
devshm               1007M   12K 1007M   1% /dev/shm
lrm                  1007M   43M  965M   5% /lib/modules/2.6.24-16-generic/volatile
overflow              1.0M   48K  976K   5% /tmp

I should mention the OS is Hardy, computer is AMD64 CPU is 6400+ 2 gig ram radeon hd2600xt video

Thanks,

Theo

---

### Post by chrisccoulson on 2008-05-18
Your root filesystem is definately full. From a terminal, can you try the following:
```
sudo apt-get clean
```
...this will clear out your package archive. This might free up enough space to get stuff up and running again so you can figure out where else to free up space from. If this doesn't leave enough space then you can try emptying your trash:
```
rm -rf ~/.local/share/Trash/*
```

Hopefully, this should free up a bit of space. Do you know where all the space is being used? Could you post the output of:
```
sudo du -h --max-depth=1 /
```

---

### Post by kiwited on 2008-05-18
Thanks again

du: cannot access `/home/theo/.gvfs': Permission denied
46G    /home
4.0K    /srv
76K    /dev
41G    /var
7.4M    /opt
6.3M    /bin
7.9M    /sbin
19M    /boot
4.0K    /initrd
16K    /lost+found
3.7M    /lib32
13M    /etc
26M    /root
4.0K    /mnt
12K    /media
du: cannot access `/proc/6810/task/6810/fd/3': No such file or directory
du: cannot access `/proc/6810/task/6810/fdinfo/3': No such file or directory
du: cannot access `/proc/6810/fd/3': No such file or directory
du: cannot access `/proc/6810/fdinfo/3': No such file or directory
0    /proc
2.3G    /usr
194M    /lib
44K    /tmp
0    /sys
89G    /

I have looked at the /var folder and there are three files that seem to be the problem:
 syslog.0 13.3 GB
messages.0 13.3 GB
kern.log.0 13.3 GB

All plain text documents dated same time and date (Sun 18 May 2008 07.57:10 NZST)
This was about when the update occurred.

Theo

---

### Post by Gunman1982 on 2008-05-18
You found those files in /var/log/ or? At least thats where they should be. You can delete them since they are just log messages, but I guess it would be interesting to look into them to see what made the logs pile up so much.
You can use the command 'tail -n 20 /var/log/messages.0' to see the 20 last lines of the file.

---

### Post by chrisccoulson on 2008-05-18
Seems like something is flooding your logs. Deleting them probably won't make the problem go away. Can you post a few lines from the end of those logs?

---

### Post by kiwited on 2008-05-18
This is the output:

May 18 07:56:46 theo-desktop kernel: [97753.828721] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.828723] attempt to acce access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841719] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.841721] attempt to access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841722] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.841724] attempt to access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841725] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.841726] attempt to access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841727] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.841729] attempt to access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841730] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.841732] attempt to access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841733] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.841734] attempt to access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841735] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.841737] attempt to access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841738] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [97753.841740] attempt to access beyond end of device
May 18 07:56:46 theo-desktop kernel: [97753.841741] sr0: rw=0, want=1791396, limit=1428096
May 18 07:56:46 theo-desktop kernel: [977theo@theo-desktop:~$ 

Theo

---

### Post by chrisccoulson on 2008-05-19
Is it entries like that which are filling your log? Do you know what device /dev/sr0 is?

---

### Post by kiwited on 2008-05-19
Do you know of any way of telling what this device is?

I have a number of problems that may be related. At boot up the computer takes a long time at the hardware abstraction layer and bluetooth sections (I think) trying to set up the USB ports, and failing. There is also a string of references to dead devices and scsi. I believe these are possibly to do with the kernel as all my USB devices work fine under a Feisty live cd but absolutely nothing works with Hardy.

I also have a problem with the Radeon video, which at least works under Hardy, but is awfully slow with effects enabled.

Does this help?

Theo

---

