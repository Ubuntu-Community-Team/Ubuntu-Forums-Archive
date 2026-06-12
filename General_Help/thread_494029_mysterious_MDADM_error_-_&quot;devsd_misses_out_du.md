---
title: "mysterious MDADM error - &quot;/dev/sd* misses out due to wrong homehost&quot;"
date: 2007-07-06
forum: General Help
---

### Post by mkramer on 2007-07-06
I'm having a hell of a time getting a RAID 5 array built.  Starting from a clean and perfectly functional install of ubuntu-server-7.04-alternate text install, I have gone from 60 to 0 in ten seconds flat.

I've set it up three times, and each time it creates just fine: after creation, I can watch it rebuild the spare drive in /proc/mdstat, I can mkfs.ext3 to the special device /dev/md0, and I can mount /dev/md0 to a directory.  Things go south when I reboot. 

When I reboot, I get something like this this

```

Starting up...
Loading, please wait...
mdadm: no devices listed in conf file were found
.....

```
Startup then procedes.  The next issue is at 
```

loading hardware drivers...

```
which can take as many as ten minutes.  Additionally,
```

Activating swap...

```
fails.  Somehow mdadm is breaking my swap file on a drive that it isn't supposed to have touched.  I can't imagine why; the installation is on an entirely separate disc from the array: the os installation is supposed to be on /dev/hda1-3 and the raid array is supposed to comprise /dev/sd{a,b,c,d,e,f} (no partitions; just the entire drive).

Probably because the swap partition fails, the system boots extremely slowly (~20 minutes).  Before it finished booting it gives the error: out of memory and kills the mdadm process which seems to be hogging all of the memory.  Later in the login sequence it activates "mdadm --monitor", but I don't know if that is the same process that it kills in order to free up memory to boot.  At this point in the login sequence, I am already over my head.

Anyway, it eventually boots up.  When it does, I am greeted with a login shell.  After I login,

```

#df -h
FS        Size   Used      Avail   Use%   Mounted on
/dev/hda1 37G    733M      35G     3%     /
...
/dev/hda2 14G    164M      13G     2%     /home

```
My swap partition, hda3, does not appear.  I don't know how to fix that one.  (Do you?)

Furthermore,

```

mdadm --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active

```

```

#cat /proc/mdstat
md0: inactive sdb[1](S) sde[5](S) sdd[3](S) sdc[2](S)
...
unused devices: <none>

```
This is where things get really weird.  /proc/mdstat shows that mdadm sees some of my block devices but not all of the ones that are supposed to be there.  
But the ones that it sees change from reboot to reboot!  

I.E., sometimes when I reboot, it sees sdb,c,d; sometimes it sees sda,c,f,d etc.  In the fifteen or so reboots that I've done, it's never found them all and successfully assembled the array.  But the drives are there.  They are all successfully detected by the BIOS, and
```

#ls /dev | grep sd 
sda
sdb
sdc
sdd
sde
sdf

```.

So now I figure, let's try it manually.
```

# mdadm --stop /dev/md0
mdadm: stopped /dev/md0

#cat /proc/mdstat
Personalities : [raid6][raid5][raid4]
unused devices: <none>

#mdadm --assemble /dev/md0 /dev/sd{a,b,c,d,e,f}
mdadm: /dev/sdb misses out due to wrong homehost
mdadm: /dev/sdc misses out due to wrong homehost
mdadm: /dev/sdd misses out due to wrong homehost
mdadm: /dev/sde misses out due to wrong homehost
mdadm: /dev/md0 assembled from 1 drive and 1 spare - not enough to start the array

```
Always, two or three of the drives work and two or three report the homehost error.  In the particular example I just ran, four reported the error.  However, which ones give errors will change from reboot to reboot (which is mysterious to me).

At this point I am completely out of my league.  What's a homehost?  I don't know, and google doesn't turn up much.  Googling the error message also doesn't turn up much.  I now humbly submit this one to the vast wisdom of the linux community.  Thanks in advance to anyone who wants to help me tackle this one.

Mason Kramer

---

### Post by mkramer on 2007-07-06
The weirdness continues.

Every nth reboot,  the boot sequence hangs at ```

*loading hardware drivers
error receiving uevent message: no buffer space available

```
Eventually it will still boot up.  The weird part is that sometimes it does it, and sometimes not.  I haven't written a single byte to the disc in fifty reboots, but I am getting different errors each time I restart.

Also, occasionally the swap file does not fail to activate, but df - h still does not show the swap file after I log in.  When the swap file does not fail to activate, the boot sequence takes less than two minutes, compared to 20 minutes when it does fail.  All of this, and I haven't changed a single byte!

---

