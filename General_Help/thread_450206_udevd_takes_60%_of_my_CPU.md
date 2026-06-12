---
title: "udevd takes 60% of my CPU"
date: 2007-05-21
forum: General Help
---

### Post by damotor on 2007-05-21
Hello.
I recently updated from dapper to breezy and there to feisty, almost everything was ok and I was able to solve the problems I found. Now, my problem is that after a while there's a process in my computer called /sbin/udevd -daemon that consumes 60% of my CPU all the time and taking into account that I work with a laptop it is a big problem since it reduces my battery and makes my laptop work all the time.
Here is the output of top without any additional programs running:
```
Tasks: 109 total,   4 running, 105 sleeping,   0 stopped,   0 zombie
Cpu(s): 68.6%us, 15.1%sy,  0.0%ni,  9.7%id,  3.7%wa,  0.3%hi,  2.7%si,  0.0%st
Mem:   1035656k total,   994764k used,    40892k free,    17208k buffers
Swap:  1951856k total,   164376k used,  1787480k free,   631608k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 2573 root      21  -4  148m 146m  364 S **67.6** 14.5   1232:37 udevd                                                                                           
 5631 root      15   0 98.5m  65m 8024 S  0.7  6.5  20:34.32 Xorg                                                                                            
 7027 yo        15   0 41360 5208 4024 S  0.3  0.5   3:26.13 gkrellm                                                                                         
27398 yo        15   0  2320 1168  880 R  0.3  0.1   0:00.01 top                                                                                             
27603 root      23  -2  148m 147m  460 R  0.3 14.6   0:00.01 udevd                                                                                           
    1 root      23   0  2380  472  428 S  0.0  0.0   0:01.25 init                                                                                            
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                     
    3 root      34  19     0    0    0 S  0.0  0.0   0:01.34 ksoftirqd/0                                                                                     
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                                                      
    5 root      10  -5     0    0    0 S  0.0  0.0   0:01.10 events/0                                                                                        
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper                                                                                         
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread                                                                                         
   30 root      10  -5     0    0    0 S  0.0  0.0   0:01.33 kblockd/0                                                                                       
   31 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kacpid                                                                                          
   32 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                                                    
  123 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 kseriod                                                                                         
  144 root      16   0     0    0    0 S  0.0  0.0   0:00.40 pdflush                                                                                         
  145 root      10  -5     0    0    0 S  0.0  0.0   0:03.13 kswapd0                                                                                         
  146 root      14  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                                                           
 1818 root      15   0     0    0    0 S  0.0  0.0   0:01.12 pdflush                                                                                         
 1905 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                                                   
 1908 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                           
 2041 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khpsbpkt                                                                                        
 2070 root      10  -5     0    0    0 S  0.0  0.0   0:54.02 ata/0                                                                                           
 2071 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                                                         
 2171 root      19  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                       
 2172 root      10  -5     0    0    0 S  0.0  0.0   1:48.87 scsi_eh_1                                                                                       
 2225 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 knodemgrd_0                                                                                     
 2354 root      10  -5     0    0    0 S  0.0  0.0   0:09.66 kjournald                                                                                       
 3425 root      17  -5     0    0    0 S  0.0  0.0   0:00.00 kpsmoused                                                                                       
 3436 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                                                                                         
 3465 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 pccardd                                                                                         
 3528 root      10  -5     0    0    0 S  0.0  0.0   0:42.28 ipw2200/0
```

Using htop I realize that /sbin/udevd -daemon takes a lot of CPU but /lib/udev/watershed /sbin/evms_activate can also take up to 100% some times.

Thanks for your help.

---

### Post by DoctorMO on 2007-05-21
take a look at dmesg and see if you have a lot of kernel messages.

have you tried killing udev? as much as this would hurt hardware refreshing and mounting (you can always reboot to get it back) use killall command.

---

### Post by kernco on 2007-06-26
I have this too running Gutsy.  dmesg contains the same two lines repeated:
[  561.830591] device-mapper: table: 254:1: linear: dm-linear: Device lookup failed
[  561.831009] device-mapper: ioctl: error adding target to table

This is happening on a desktop for me.  It's only taking about 25% of the CPU for me, but it significantly slows down the system because it's nice -4.  "killall udevd" works, but it's not the optimal solution since I have to restart whenever I want to connect a new device.

---

### Post by Rubbing Alcohol on 2007-07-31
Im having similar issues too. udevd takes a steady 20% which forces my CPU to stay at 100%, not great when I'm battery. Killing udevd makes the machine work normally enough, but has anyone found a better fix?

As a side-note, it also seems to be scanning the hdd a lot. The hdd usage LED is constantly flickering.

Like I said, as soon as I killall udevd, everything goes back to normal.

---

### Post by mcg on 2007-07-31
This started happening to me as well. It looks like the latest Gutsy kernel switched from IDE to SCSI devices for drives yet again!  It seems Ubuntu can't make up its mind to use IDE or SCSI devices.  To fix this problem, I had to change the devices in /etc/fstab to point to valid SCSI devices(/dev/hda becomes /dev/sda,etc....)

---

### Post by Rubbing Alcohol on 2007-08-03
I just tried this now.

It does reduce the CPU utilisation of udevd, but my CPU still won't throttle down and the hard drive is still spinning constantly.

Again, killall udevd fixes the problems.

To anybody that might have an idea of how to fix this, is there any more information I can giev that would be helpful?

---

### Post by mcg on 2007-08-07
See [bug 115616]("https://bugs.launchpad.net/ubuntu/+source/evms/+bug/115616") for what looks like your/our problem.  According to the bug the temporary "fix" until the bug is fixed is to remove the EVMS package.  If you're using EVMS then you'll need to wait for EVMS to be fixed.

---

### Post by dgavenda on 2007-10-20
I have the same exact problem on both a desktop and laptop.  Both were upgraded from 7.04 and both xubuntu.  The laptop has nothing plugged into it.

The problem stops when I stop udevd and restart it.  So it seems there may be a bug that still exists.

---

### Post by torstenaf on 2007-11-20
After upgrading to 7.10, had the same problem with **udevd** and _high CPU_ usage and my system _slowed to a crawl_.

In addition, **dmesg** was showing hundreds of strange errors accessing the drive.

I implemented the temp fix suggested by **mdg,** to remove _evms_ package, and my laptop is working normally.

Thanks!
-T

---

### Post by ratsbane on 2007-12-10
I had the same problem in upgrading to 7.10 - udevd takes close to 100% of CPU.  I tried the suggestion from mcg above and it seems to have at least partially fixed the problem:
" I had to change the devices in /etc/fstab to point to valid SCSI devices(/dev/hda becomes /dev/sda,etc...."

I edited the fstab file:
[FONT="Courier New"]sudo vim /etc/fstab[/FONT]

and noted the comments:

[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 -- converted during upgrade to edgy
UUID=4488d9b5-004f-46b2-a188-f691a5ab4963 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=35ecf953-ac04-4861-bd85-03b908cea662 none swap sw 0 0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0[/FONT]

I uncommented the lines that the upgrade had inserted, commented the comments (at the ends of lines) that upgrade inserted and restarted the computer. Udevd is now < 1% CPU at the most.


[FONT="Courier New"]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
 /dev/sda1 #-- converted during upgrade to edgy
#UUID=4488d9b5-004f-46b2-a188-f691a5ab4963 / ext3 defaults,errors=remount-ro 0 1
 /dev/sda5 #-- converted during upgrade to edgy
#UUID=35ecf953-ac04-4861-bd85-03b908cea662 none swap sw 0 0
#/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0[/FONT]


The DVD drive started seeking every few minutes after the upgrade, whether I put a disk in or not.  It makes an annoying buzzing sound.  These changes didn't help that.  (Note that I also tried commenting out the last line: /dev/cdrom  

I don't totally understand what's going on here but this is working much better now.

Thanks for the suggestion!

---

### Post by merlinesq on 2007-12-26
I had similar problems when upgrading from 7.04 to 7.10, with udevd taking all my CPU and I was unable to properly access a FAT 32 partition (an historical hangover) I was using to store music etc.  

Found some useful advice at [URL="http://codepoets.co.uk/upgrade-ubuntu-gutsy-emvs-and-udevd-100-cpu-usage-aka-udevd-going-nuts"]

In my case a definite problem with evms and udevd.  I used apt-get remove evms, and then had to kill the udevd process as udevd stop would not work.  Then tried udevd stop and udevd start.

Restarted machine and lo, no background CPU usage and access to the FAT 32 partition

So problem solved (albeit not the sort of process I expect to have to go through after an automated upgrade - previous upgrades have been straighforward), but it would be nice if someone could explain what the problem actually is, and whether removing evms is going to cause me any other problems in the future ?.

---

### Post by totalsecrecy on 2008-01-01
**This post could be related to an Ubuntu bug filed at**: 119315 [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				:confused: Strange enough, I do not have the evms packet installed and I still show a gazillion udevd processes with at least (1) of them at 100% and another between 20-50%. I do have libdevmapper installed. Does this initiate udevd processes?

I attempted to remove this packet, but many other programs warned me that they depended on it (libdevmapper is utilized by amarok et. al.)
Each time I restart my machine, I must "$ sudo killall udevd" to stop all of the processes and then restart the daemon "$ udevd" and the CPU is at ~1%! :)

Not an elegant solution, but it's all I can do for now.

---

### Post by centyx on 2008-02-14
> **merlinesq said:**
> 
In my case a definite problem with evms and udevd.  I used apt-get remove evms, and then had to kill the udevd process as udevd stop would not work.  Then tried udevd stop and udevd start.


Much thanks to this thread. I've got a cheap server at Layered Tech and had them replace the old CentOS 3 with Ubuntu 6.0.6 LTS last week. I immediately upgraded to Gutsy ( up one release at a time ). Yesterday I noticed that a few packages had been kept back. I did another aptitiude safe, then full-upgrade, and evms was replaced in the procss. Ever since udevd has been eating 99% CPU.

I didn't have any need for evms, so I removed it, rebooted with the newly generated initramfs, and all is well.

---

