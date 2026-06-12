---
title: "mdadm and SSD performance degradation over time"
date: 2014-10-08
forum: General Help
---

### Post by arieunier on 2014-10-08
Hi there
My raid 5 array using mdadm is showing performance degradation overtime .. And my SSD as well
The raid has 6 3Tb drives :
```
koko@DATA:~$ sudo mdadm --detail /dev/md0 
/dev/md0:
        Version : 1.2
  Creation Time : Sat Feb  9 16:57:14 2013
     Raid Level : raid5
     Array Size : 14650677440 (13971.98 GiB 15002.29 GB)
  Used Dev Size : 2930135488 (2794.40 GiB 3000.46 GB)
   Raid Devices : 6
  Total Devices : 6
    Persistence : Superblock is persistent


    Update Time : Wed Oct  8 10:30:57 2014
          State : active 
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 64K


           Name : DATA:0
           UUID : aed04bbb:c2f54929:5e59ae48:bd8aa971
         Events : 512367


    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde
       7       8       80        4      active sync   /dev/sdf
       6       8       96        5      active sync   /dev/sdg

```

When performing some writing/reading tests, i see the performance are lower that what they used to be (it used to be around 300MB/S on both drives)
```

/dev/sda:
 Timing cached reads:   5486 MB in  2.00 seconds = 2743.76 MB/sec
 Timing buffered disk reads: 1158 MB in  3.00 seconds = 385.59 MB/sec


/dev/md0:
 Timing cached reads:   5586 MB in  2.00 seconds = 2794.05 MB/sec
 Timing buffered disk reads: 1854 MB in  3.00 seconds = 617.98 MB/sec
WRITING tests
SSD
4294967296 bytes (4.3 GB) copied, 40.4634 s, 106 MB/s
RAID
4294967296 bytes (4.3 GB) copied, 19.1494 s, 224 MB/s


Copying from Raid to SSD
Copying 4.00 GiB 100%  133.48 M/s Time: 00:00:32
Copying from SSD to RAID
Copying 4.00 GiB 100%  163.33 M/s Time: 00:00:26

```

My system runs a few VM at the same time, maybe it has some impact, but they're not using a lot of resources.. 
Someone knows what could be the cause, and how to solve that ?

---

### Post by tgalati4 on 2014-10-08
How full are both disks?

Writing speeds tend to degrade on SSD because of wear-leveling by the SSD controller.  Not much you can do about that.  The read speeds seem OK on both the SSD and RAID5.

The RAID5 slowdown could be a RAM issue.  How much RAM do you have and how much is used with your VM's running?

```
free
```

It's possible that large writes in a low-RAM environment would be slower.  How fast are 1 GB writes?  How fast are 100 MB writes?  Are these speeds from a fresh-boot system, or one running for 180 days?

How often do you perform 4 GB writes?  What is the lowest speed that you will tolerate?

Look through your log files (/var/log/syslog) for any disk-related errors.  It's possible that kernel's paging system is having problems serving both the VM's and the RAID5.

I would get friendly with *iostat*.  Obviously solving the problem requires identifying the problem:  [http://www.thegeekstuff.com/2011/07/iostat-vmstat-mpstat-examples/](http://www.thegeekstuff.com/2011/07/iostat-vmstat-mpstat-examples/)

---

### Post by arieunier on 2014-10-09
Hi
I don't perform these tests quite often. I just realized the system was slow when performing network copy (used to reach more than 100MB/S before, not now..)
Here are the results of the commands you asked for :
```

koko@DATA:~$ iostat 
Linux 3.5.0-17-generic (DATA) 	10/09/2014 	_x86_64_	(4 CPU)


avg-cpu:  %user   %nice %system %iowait  %steal   %idle
           9.69    0.25   11.06    0.55    0.00   78.45


Device:            tps    kB_read/s    kB_wrtn/s    kB_read    kB_wrtn
sda              13.19        24.85       276.95   25296703  281923596
sdb              20.32      3132.33       253.51 3188611421  258063541
sdc              20.13      3132.63       251.55 3188914392  256065457
sdd              20.17      3133.25       251.54 3189540896  256063769
sde              20.11      3133.03       249.70 3189321332  254186537
sdf              20.15      3131.83       252.00 3188104492  256528557
sdg              20.18      3131.33       252.83 3187591256  257376037
md0              58.01      1269.66      1198.75 1292474941 1220284504


koko@DATA:~$ uptime
 16:01:31 up 11 days, 18:46,  2 users,  load average: 1.20, 1.79, 2.91
koko@DATA:~$ df
Filesystem       1K-blocks       Used  Available Use% Mounted on
/dev/sda1         45583392   10065500   33202324  24% /
udev               7932376          8    7932368   1% /dev
tmpfs              1588420       2356    1586064   1% /run
none                  5120          0       5120   0% /run/lock
none               7942100          4    7942096   1% /run/shm
none                102400          8     102392   1% /run/user
/dev/md0       14535239968 8530051996 6005187972  59% /storage


top - 16:03:50 up 11 days, 18:48,  2 users,  load average: 1.14, 1.57, 2.67
Tasks: 186 total,   1 running, 185 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.7 us, 10.9 sy,  0.3 ni, 78.4 id,  0.5 wa,  0.0 hi,  0.2 si,  0.0 st
KiB Mem:  15884200 total, 15726160 used,   158040 free,   422388 buffers
KiB Swap: 16208892 total,   606828 used, 15602064 free, 14007620 cached

```

I did not find any error/kernel messages interesting in all the syslogs file i have ..
```

root@DATA:/var/log# grep -i kernel syslog*
syslog:Oct  9 13:31:39 DATA kernel: [1008734.496900] /dev/vmnet: open called by PID 30282 (vmx-vcpu-0)
syslog:Oct  9 13:31:39 DATA kernel: [1008734.496913] /dev/vmnet: port on hub 0 successfully opened
syslog.1:Oct  8 09:25:24 DATA kernel: [907584.002733] /dev/vmnet: open called by PID 6285 (vmx-vcpu-0)
syslog.1:Oct  8 09:25:24 DATA kernel: [907584.002749] /dev/vmnet: port on hub 0 successfully opened
syslog.1:Oct  9 07:46:34 DATA kernel: [988034.600310] type=1400 audit(1412833594.964:61): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=20059 comm="apparmor_parser"
syslog.1:Oct  9 07:46:34 DATA kernel: [988034.601117] type=1400 audit(1412833594.964:62): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=20059 comm="apparmor_parser"
root@DATA:/var/log# grep -i error syslog*
syslog:Oct  9 08:51:51 DATA pptpd[6217]: CTRL: EOF or bad error reading ctrl packet length.
syslog:Oct  9 12:16:47 DATA pptpd[946]: CTRL: EOF or bad error reading ctrl packet length.

```

---

### Post by tgalati4 on 2014-10-09
Your system has 10 to 11% of its CPU cycles for system services (probably handling the virtual machines).  Your CPU load is over 1.0.  This could be a false reading, or a real reading if there is a system call that is causing interrupts and giving the impression of waiting instructions.

Your 16GB is all in use and you are now running into swap.  That can slow down many operations--paging from swap is slow and painful.

I would reboot, stop the vm's and test the 4 GB file sizes.  Then I would then test the smaller file sizes, 2GB, 1GB, 0.5GB, 0.25GB and see if there is a correlation.  Make sure swap shows 0 Bytes Used when you run your tests.

Network throughput adds another layer of complexity.

---

### Post by arieunier on 2014-10-09
I've shut all VM down, and re tested. The raid performed better. Then rebooted, and restarted the tests
```

koko@DATA:~/SCRIPT$ ./testDrives.sh 
[sudo] password for koko: 


/dev/sda:
 Timing cached reads:   5684 MB in  2.00 seconds = 2843.00 MB/sec
 Timing buffered disk reads: 1232 MB in  3.00 seconds = 410.13 MB/sec


/dev/md0:
 Timing cached reads:   5984 MB in  2.00 seconds = 2992.80 MB/sec
 Timing buffered disk reads: 1816 MB in  3.00 seconds = 605.15 MB/sec
WRITING tests
SSD
4096+0 records in
4096+0 records out
4294967296 bytes (4.3 GB) copied, 41.61 s, 103 MB/s
RAID
4096+0 records in
4096+0 records out
4294967296 bytes (4.3 GB) copied, 18.4762 s, 232 MB/s
unix:abstract=/tmp/dbus-ZIshkICOIX,guid=3b4c2da9af6651daa4f106425436dd30
31746
Copying from Raid to SSD
Copying 4.00 GiB 100% |#########################################################################################################################################################################| 143.08 M/s Time: 00:00:30
Copying from SSD to RAID
Copying 4.00 GiB 100% |#########################################################################################################################################################################| 293.44 M/s Time: 00:00:14
koko@DATA:~/SCRIPT$ sudo reboot
-------------
koko@DATA:~/SCRIPT$ ./testDrives.sh 
[sudo] password for koko: 


/dev/sda:
 Timing cached reads:   6160 MB in  2.00 seconds = 3081.49 MB/sec
 Timing buffered disk reads: 1234 MB in  3.00 seconds = 410.84 MB/sec


/dev/md0:
 Timing cached reads:   6064 MB in  2.00 seconds = 3033.46 MB/sec
 Timing buffered disk reads: 1564 MB in  3.00 seconds = 520.86 MB/sec
WRITING tests
SSD
4096+0 records in
4096+0 records out
4294967296 bytes (4.3 GB) copied, 39.4243 s, 109 MB/s
RAID
4096+0 records in
4096+0 records out
4294967296 bytes (4.3 GB) copied, 20.4251 s, 210 MB/s
unix:abstract=/tmp/dbus-veQK90qy0r,guid=4bdd42e175be511b8558c0a85436de33
5066
Copying from Raid to SSD
Copying 4.00 GiB 100% |#########################################################################################################################################################################| 145.99 M/s Time: 00:00:29
Copying from SSD to RAID
Copying 4.00 GiB 100% |#########################################################################################################################################################################| 291.90 M/s Time: 00:00:14
koko@DATA:~/SCRIPT$ 

```

Maybe i should plan a weekly reboot, shut down VM, or invest in a dedicated VM environment.

---

