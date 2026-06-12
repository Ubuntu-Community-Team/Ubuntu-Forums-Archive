---
title: "Cannot acces to top level folder /"
date: 2014-10-27
forum: General Help
---

### Post by doomy2 on 2014-10-27
Hello,
sometimes i am cannot access to top level directory, the ls /, df, cd / command freezes, without any error messages. Any other folders is normally accessible. After reboot is folder / accessible.
This occurs under user and also root account. The system SSD disk is new, without errors.
I do not know where to find the cause, please help (sorry for my english).

Row from /etc/fstab file for system disk
```
UUID=1fb007ea-2fc6-4b8d-bfc9-279b4501de34 /               ext4    noatime,commit=600,errors=remount-ro 0       1
```

Doomy
Ubuntu 14.04.1 LTS

---

### Post by TheFu on 2014-10-27
I'm afraid that the most likely issue is the SSD is unavailable - likely to be failing - unless there is another disk that is mounted and should be available, but is not.

For example, I use autofs (automounter) to dynamically mount storage .... some is USB, some is NFS .... if I try to CD into the place where that storage should and it isn't available, that shell will lock up.  If storage had successfully been mounted, has not timed out, but is unavailable, then any 'df' call or 'du' call that refers to that storage location will lock up too. .... 

So - what does all this mean?  If cd / doesn't work ... it is likely because the partition providing storage as / is not available - the SSD. If it is not available, check the fstab settings very carefully and check the log files for any errors.  Good luck.

Oh ... and I'd ensure the backups are 100% too.

---

### Post by doomy2 on 2014-10-27
Thank for answer TheFu. I will add information:
- same problem was on the older ssd disk, so I bought a new SSD hard drive
- cd / not work, but cd /var, or cd /home, or cd /root etc. works
- all folders (/, /var, /home, /root) are on the same partition
Unfortunately, do not even know what to look in the log files.
Please, any other tips?

---

### Post by nerdtron on 2014-10-27
What is the error when you "cd /" ? How about on the file browser? Is there any other disk in this system other your SSD?
What is the output of "ls -lah /" ?

---

### Post by TheFu on 2014-10-27
> **doomy2 said:**
> Thank for answer TheFu. I will add information:
- same problem was on the older ssd disk, so I bought a new SSD hard drive
- cd / not work, but cd /var, or cd /home, or cd /root etc. works
- all folders (/, /var, /home, /root) are on the same partition
Unfortunately, do not even know what to look in the log files.
Please, any other tips?

Ok - first, check the log files.  [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)
There may be a GUI way to accomplish this - dunno - no GUI on servers.

Is there any chance that the permissions were changed, even by accident?  On a multiple user system (like Linux/ubuntu/fedora/mint/redhat/centos/....), file permissions are absolutely critical.

Before it stops working, please post the output from **df -h** - use **code tags** please, not an image.

---

### Post by doomy2 on 2014-10-28
thank you for tips.
Commands ls, cd, df etc. freezes without error messages.
Here is output from df -h
```

File system              Size Used Free Used% P&#345;ipojeno do
/dev/sdc1                          25G   12G   12G  50% /
none                              4,0K     0  4,0K   0% /sys/fs/cgroup
udev                              2,9G  4,0K  2,9G   1% /dev
none                              3,0G   60K  3,0G   1% /tmp
tmpfs                             597M  1,9M  595M   1% /run
none                              5,0M     0  5,0M   0% /run/lock
none                              3,0G   74M  2,9G   3% /run/shm
none                              100M   24K  100M   1% /run/user
/dev/md0                          917G  421G  450G  49% /DISK_D
192.168.2.133:/volume1/zalohy     914G  471G  444G  52% /DISK_Z



```

---

### Post by TheFu on 2014-10-28
So ... you are using an SSD, RAID and NFS.
I'd check 
* /proc/mdstat
* errors and warning in the log files - always check this
* boot off a liveCD/USB media and run **fsck** on /dev/sdc1
* verify that your nfs mount options are not HARD ... which will lock up the client NFS machine if the server NFS server is unavailable. If any part of this connection is over wifi - use soft, not hard links and set a reasonable timeout parameter.

From here, it doesn't seem like much is wrong ... at this point. OTOH, guessing what a problem is without any facts is hard. l)

---

### Post by doomy2 on 2014-10-29
thank for all. Problem has a cause (probably) in the mount point /DISK_Z for NFS disk. 
When the NFS disk was unavailable on the network, then top level directory was un[COLOR=#000000]accessible.[/COLOR]
I am moved mount point to location /mnt/DISK_Z, I think that solved it.

---

### Post by TheFu on 2014-10-29
a) Thanks for reporting the solution found

b) Don't think that is really the issue - - because my /D nfs mount doesn't show that issue across ... er ... 6 client systems.

```
$ df .
Filesystem      Size  Used Avail Use% Mounted on
istar:/D        3.5T  3.0T  376G  89% /D
```

However, there is a difference.  I use autofs on the client-side to control mounts, not the fstab.

There are other similar mounts on my network for this too ... again, I use autofs and for those I even force hard mounts.  Here's an auto.nfs config line for one of them:
```
/VMs -fstype=nfs,hard,intr,rw,async,vers=3  romulus:/raid/media/VMs
```

The export stuff on the server-side is the same as already recommended above.

---

