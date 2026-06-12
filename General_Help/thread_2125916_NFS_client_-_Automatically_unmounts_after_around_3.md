---
title: "NFS client - Automatically unmounts after around 30 minutes (not using automount)"
date: 2013-03-15
forum: General Help
---

### Post by pcharby on 2013-03-15
The mount point disappears 30 minutes (or so) after mounting it. It doesn't matter if I'm in the middle of a file transfer, using the mount point, or what's going on.
For example, in the middle of a file transfer, I'll see a "Permission Denied. Cannot write to /media/nas/" or something similar.
Then when doing a df -h, the mount point is no longer visible. ls -l /media, I see a bunch of question marks instead of file permissions etc.
There are no errors from dmesg or /var/log/syslog. Also, no errors on the NAS box. 

No problem mounting either.



New 12.04 64 bit install.
Mount a share from DNS-320 NAS.
From Linux server:

showmount -e 192.168.1.xxx
Export list for 192.168.1.xxx:
/mnt/HD/HD_a2     *
/mnt/HD/HD_a2/P2P *

/etc/fstab entry
192.168.1.xxx:/mnt/HD/HD_a2 /media/nas nfs rw,hard,intr 0 0



Any ideas? 

Thanks

---

### Post by rnerwein on 2013-03-15
hi
running the same version. got no problems with nfs. the only different is my mount isn't interupable "intr". the hard link is ok for read/write.
your entry:
/etc/fstab entry
192.168.1.xxx:/mnt/HD/HD_a2 /media/nas nfs rw,hard,intr 0 0
there for i think on your system is an interrupt coming in (from where for ever - don't no). 
try the mount without the "intr" option. i guess there is the problem.
my entry:
/etc/fstab entry:
192.168.2.xxx:/mnt/gonzos/home nfs rw,hard 0 0
i know there is a big problem when the client comes up and the server isn't available. but give the non inrt a try and see what's happen.
ciao

---

### Post by pcharby on 2013-03-15
Thanks. Trying that now. 
One thing I didn't try was a power recycle on the NAS. Doing that at the same time.

I'll have to wait ~30 minutes to see if it works.........

---

