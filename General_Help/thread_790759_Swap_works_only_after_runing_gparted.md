---
title: "Swap works only after runing gparted ???"
date: 2008-05-11
forum: General Help
---

### Post by danial-aalee on 2008-05-11
Hi,

yes, you can laugh but that is how it goes.  Few weeks ago I was able to mount swap partition but then I realized that it actually works only after gparted (noticed thru System monitor KDE4).  Here are the results of top, system monitor and fdisk -l:  pre and post of running gparted.  I already attached a text file named top-results compared.txt with this message. 

**fdisk -l results:**
Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02b602b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3188    25607578+   7  HPFS/NTFS
/dev/sda2            3189        4463    10241437+   7  HPFS/NTFS
/dev/sda3            4464        5738    10241437+  83  Linux
/dev/sda4            5739        7299    12538732+   f  W95 Ext'd (LBA)
/dev/sda5            5739        7013    10241406   83  Linux
/dev/sda6            7014        7299     2297263+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
240 heads, 63 sectors/track, 26342 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00098133

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3878    29317648+   7  HPFS/NTFS
/dev/sdb2   *        3879       26342   169827840    f  W95 Ext'd (LBA)
/dev/sdb5            3879        6463    19542568+   7  HPFS/NTFS
/dev/sdb6            6464       10339    29302528+   7  HPFS/NTFS
/dev/sdb7           10340       11631     9767488+   7  HPFS/NTFS
/dev/sdb8           11632       18090    48830008+   7  HPFS/NTFS
/dev/sdb9           18091       26342    62385088+   7  HPFS/NTFS
guru@guru-desktop:~$ 



**top command results: {before gparted ran}**

top - 15:55:47 up  2:15,  2 users,  load average: 0.00, 0.03, 0.08
Tasks:125 total, 1 running, 124 sleeping, 0 stopped, 0 mzombie 

Cpu(s): 5.2%us, 1.3% sy, 0.7% ni, 91.9% id, 0.9% wa, 0.0% hi, 0.0% si, 0.0% st
Mem: 1804752k total, 815032k  used, 989720k  free, 24676k  buffers 
Swap: 2297252k  total, 0k  used, 2297252k  free, 413008k  cached 

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             
5542 root      20   0  142m  54m 8040 S   10  3.1   7:05.77 Xorg                
6860 guru      20   0  258m  29m  20m S   10  1.7   5:03.43 ksysguard           
6863 guru      20   0 32508 1648 1040 S    6  0.1   1:43.20 ksysguardd          
6952 guru      20   0 18980 1188  864 R    4  0.1   0:00.02 top                 
   1 root      20   0  4016  880  592 S    0  0.0   0:01.00 init                
   2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd            
   3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0         
   4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0         
   5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0          
   6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1         
   7 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1         
   8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1          
   9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0            
  10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1            
  11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper             
  45 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0           
  46 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/1

 - 15:55:50 up  2:15,  2 users,  load average: 0.00, 0.03, 0.08 
Tasks: 125  total,   2  running, 123  sleeping,   0  stopped,   0  zombie 
Cpu(s):  2.6% us,  0.3% sy,  0.0% ni, 96.9% id,  0.0% wa,  0.0% hi,  0.2% si,  0.0% st 
Mem:   1804752k  total,   815048k  used,   989704k  free,    24676k  buffers 
Swap:  2297252k  total,        0k  used,  2297252k  free,   413012k  cached 

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             
6860 guru      20   0  258m  29m  20m S    3  1.7   5:03.51 ksysguard           
5542 root      20   0  141m  54m 8040 S    2  3.1   7:05.83 Xorg                
6863 guru      20   0 32508 1648 1040 S    1  0.1   1:43.22 ksysguardd          
   1 root      20   0  4016  880  592 S    0  0.0   0:01.00 init                
   2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd            
   3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0         
   4 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0         
   5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0          
   6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1         
   7 root      15  -5     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1         
   8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1          
   9 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/0            
  10 root      15  -5     0    0    0 S    0  0.0   0:00.04 events/1            
  11 root      15  -5     0    0    0 S    0  0.0   0:00.00 khelper             
  45 root      15  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0           
  46 root      15  -5     0    0    0 S    0  0.0   0:00.04 kblockd/1          
  49 root      15  -5     0    0    0 S    0  0.0   0:00.00 kacpid              

** Results from System Monitor (KDE4) {before gparted ran}**
Physical Memory: runing 125 process
Application Memory:    0.32 G
Cached Memory:        0.37 G
Buffer Memory:        0.02 G
=======================

** post gparted results for top and system information:**

** top:**
top - 16:23:32 up  2:42,  2 users,  load average: 0.72, 0.32, 0.17
Tasks:132 total, 1 running, 131 sleeping, 0 stopped, 0 mzombie 

Cpu(s): 3.0%us, 0.8% sy, 0.0% ni, 90.% id, 0.0% wa, 0.0% hi, 0.0% si, 0.0% st
Mem: 1804752k total, 917528k  used, 887472k  free, 26900k  buffers 
Swap: 2297252k  total, 0k  used, 2297252k  free, 447328k  cached 


** Results from System Monitor (KDE4) {before gparted ran}:**
Physical Memory: runing 125 process
Application Memory:    0.00 G
Cached Memory:        0.42 G
Buffer Memory:        0.43 G

No swap space available

Any idea what is going on here ???  Is it me misinterpreting or system playing with my head... 

If some helping hand wants to remote in to actually see, let me know, I will reboot and will show exactly what is going on here.  please do let me know how to invite or give access for that matter.

Thanks for your time and help in this regard.

danial

---

### Post by forestpixie on 2008-05-11
Do you have a line for swap in fstab

```
cat /etc/fstab
```

---

### Post by danial-aalee on 2008-05-11
> **forestpixie said:**
> Do you have a line for swap in fstab

I am sure not, did I need to ?  Should I edit enter it in /etc/fstab ?

danial

---

### Post by danial-aalee on 2008-05-11
I guess, I misunderstood your question.  yes I do have a line for swap in /etc/fstab.  Earlier when I worked on that issue I tried, made mistakes and finally got it working and these are last few lines I have in there.  Keeping no used commands just for refrence of what is working or not working...


# changes for swaps... 
# /dev/hda6
# /dev/sda6 /media/hda6 swap sw 0 0

# *** following is the latest *** 
# /dev/sda6
# /dev/sda6 /media/sda6 swap sw 0 0
# /dev/sda6 /media/sda6 swap swap defaults  **{this is also working}**
/dev/sda6 /media/sda6 swap loop.sw 0 0

danial

---

### Post by ajgreeny on 2008-05-11
You need it in your /etc/fstab file, so by all means edit it and add a line with ```
sudo gedit /etc/fstab
```Make sure you get the line correct, however, or you could end up in a worse situation.  It may be that doing something with gparted has changed the UUID of your swap partition so firstly get the correct UUID with ```
ls -l /dev/disk/by-uuid
```and make sure you get the correct UUID for swap.  Now add a line with the following:-

UUID=69e6210a-6a82-42b3-8c3f-4fe6daa69202 none            swap    sw              0       0

Change the UUID= at the start to fit your UUID.   Hope that helps.

---

### Post by danial-aalee on 2008-05-11
> **ajgreeny said:**
> You need it in your /etc/fstab file, so by all means edit it and add a line with ```
sudo gedit /etc/fstab
```Make sure you get the line correct, however, or you could end up in a worse situation.  It may be that doing something with gparted has changed the UUID of your swap partition so firstly get the correct UUID with ```
ls -l /dev/disk/by-uuid
```and make sure you get the correct UUID for swap.  Now add a line with the following:-

UUID=69e6210a-6a82-42b3-8c3f-4fe6daa69202 none            swap    sw              0       0

Change the UUID= at the start to fit your UUID.   Hope that helps.

Thanks, let me go ahead and do it now... and I assume that I need to reboot to check...
Thanks again for your time and help...
danial

---

### Post by danial-aalee on 2008-05-11
AJ,
unfortunately, it is still doing the same way... 
I sure don't know, what is causing that.
here is the copy of ls -l:

guru@guru-desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 01C5B1E0C7899380 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 01C5B1E0CD332940 -> ../../sdb6
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 01C5B1E0CFEAF640 -> ../../sdb7
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 01C5B1E0D339D320 -> ../../sdb8
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 1A901A3B901A1DB7 -> ../../sda2
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 39706b86-d13a-4b0c-8899-ef9c10b03fbc -> ../../sda6
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 6dfd779e-99ab-4273-822c-c15654cbf3da -> ../../sda3
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 82caae3a-557a-4ffe-8a25-7d4c0d064ffb -> ../../sda5
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 BA2092E22092A543 -> ../../sda1
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 D45CF9E25CF9BEF4 -> ../../sdb9
lrwxrwxrwx 1 root root 10 2008-05-11 13:55 EA1CA3CE1CA3945B -> ../../sdb1
 
and copy of fdisk -l 
Disk /dev/sda: 60.0 GB, 60040544256 bytes
255 heads, 63 sectors/track, 7299 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02b602b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3188    25607578+   7  HPFS/NTFS
/dev/sda2            3189        4463    10241437+   7  HPFS/NTFS
/dev/sda3            4464        5738    10241437+  83  Linux
/dev/sda4            5739        7299    12538732+   f  W95 Ext'd (LBA)
/dev/sda5            5739        7013    10241406   83  Linux
/dev/sda6            7014        7299     2297263+  82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
240 heads, 63 sectors/track, 26342 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00098133

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3878    29317648+   7  HPFS/NTFS
/dev/sdb2   *        3879       26342   169827840    f  W95 Ext'd (LBA)
/dev/sdb5            3879        6463    19542568+   7  HPFS/NTFS
/dev/sdb6            6464       10339    29302528+   7  HPFS/NTFS
/dev/sdb7           10340       11631     9767488+   7  HPFS/NTFS
/dev/sdb8           11632       18090    48830008+   7  HPFS/NTFS
/dev/sdb9           18091       26342    62385088+   7  HPFS/NTFS

I do not know what other information needed?  Please guiude...
Thanks,,,
Danial

---

### Post by forestpixie on 2008-05-12
post the fstab please

---

### Post by ajgreeny on 2008-05-12
Your fstab file needs a line with the following in it:-

UUID=39706b86-d13a-4b0c-8899-ef9c10b03fbc none            swap    sw              0       0

If it isn't there, add it using gedit as root ```
sudo gedit /etc/fstab
``` and see if that helps.

---

### Post by danial-aalee on 2008-05-12
> **ajgreeny said:**
> Your fstab file needs a line with the following in it:-

UUID=39706b86-d13a-4b0c-8899-ef9c10b03fbc none            swap    sw              0       0

YES, I do have it exactly as you mentioned and instructed me to do.

Danial

---

### Post by ajgreeny on 2008-05-12
And it still doesn't mount on boot?  It certainly should do, unless the formatting as swap has been corrupted in some way.
Have a look in gparted to see if the swap partition is formatted as swap as it should be, or if it is unrecognised for some reason.  This happened to mine last week when I reset the machine after a complete freeze of the system caused by a bad DVD+RW.  I simply opened up gparted and reformatted the partition then edited fstab to the new UUID of the partition and all was well.  If everything shows up as properly formatted in gparted I think I'm at a loss about where to go from here.

---

### Post by danial-aalee on 2008-05-12
Aj,
Thanks a lot for your time and help.  If I am not wrong, yes it does show up in Gparted.  However, I will get to it later tonight (right now I am at work) and do what you mentioned and will post back. So probably, you will see it tomorrow.  Once again, I really appreciate your time.

danial.
BTW: While I am on this partititon issue, can you give me me some info about another partition I created (formatted as ext3 for extra /home stuff but Ubuntu does not use it. If I re-partition it from with in Ubuntu, can I move my home stuff to it so spare some space on root drive.
This is only, if you get a chance to do.  Thanks.

---

### Post by danial-aalee on 2008-05-13
> **forestpixie said:**
> post the fstab please

Below is the latest fstab.  It is after I re-format the swap partition with new UUID.  I have not rebooted the system yet,  but I will get back in few.

Thanks.
danial


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                                                       0  0  
# /dev/hda3
UUID=6dfd779e-99ab-4273-822c-c15654cbf3da  /               ext3         nouser,defaults,errors=remount-ro,atime,auto,rw,dev,exec,suid  0  1  
# /dev/hda1
UUID=BA2092E22092A543                      /media/hda1     ntfs         defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser        0  1  
# /dev/hda2
UUID=1A901A3B901A1DB7                      /media/hda2     ntfs         defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser        0  1  
# /dev/hda5
UUID=82caae3a-557a-4ffe-8a25-7d4c0d064ffb  /media/hda5     ext3         nouser,defaults,atime,auto,rw,dev,exec,suid                    0  2  
# /dev/hdc5
UUID=01C5B1E0C7899380                      /media/hdc5     ntfs         defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser        0  1  
# /dev/hdc6
UUID=01C5B1E0CD332940                      /media/hdc6     ntfs         defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser        0  1  
# /dev/hdc7
UUID=01C5B1E0CFEAF640                      /media/hdc7     ntfs         defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser        0  1  
# /dev/hdc8
UUID=01C5B1E0D339D320                      /media/hdc8     ntfs         defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser        0  1  
# /dev/hdc9
UUID=D45CF9E25CF9BEF4                      /media/hdc9     ntfs         defaults,nls=utf8,umask=007,uid=0,gid=46,auto,rw,nouser        0  1  
/dev/hdb                                   /media/cdrom0   udf,iso9660  user,atime,noauto,rw,dev,exec,suid                             0  0  
/dev/fd0                                   /media/floppy0  auto         user,atime,noauto,rw,dev,exec,suid                             0  0  

/dev/sdb1                                  /media/sdb1     ntfs         nls=iso8859-1,users,umask=000,ro                               0  0  

# changes for swaps... 
# /dev/hda6
# /dev/sda6 /media/hda6 swap sw 0 0

# *** following is the latest *** 
# /dev/sda6
# /dev/sda6 /media/sda6 swap sw 0 0
# /dev/sda6 /media/sda6 swap swap defaults
# /dev/sda6 /media/sda6 swap loop.sw 0 0
# UUID=39706b86-d13a-4b0c-8899-ef9c10b03fbc none swap sw 0 0
UUID=5ea03674-b869-4d27-9068-79af58a25326 none swap sw 0 0

---

### Post by danial-aalee on 2008-05-13
Okay,
I rebooted the system.  still when I am looking at System Monitor, it shows high use of Application Memory and Swap Memory sensor shows 0 use,  than I opened gparted and application memory use as well cache memory used drop to almost none and at the bottom it shows 'no swap space available'.  Gparted shows: {just to re-iterate: swap partition is under extended partition - don't know if that makes any difference or not}

partition: /dev/sda6
file system: linux-swap
mount point: {blank}
size: 2.19G
used: ---
unused: ---
flags: {blank}

Ok, so if all appears to be okay in **fstab**, **fdisk -l** and **gparted information**, I am not sure what else can be done (my little knowledge speaking here)?  Is having a swap partition necessary?  To my little knowledge, it reduces the load on physical memory but what else?   No, I am not giving up but I feel like I am wasting your time.  Instead, I should move on to my next problem and ask you on how to enable and move home folder to following (information from gparted) however, this does not show up in /etc/fstab.
partition: dev/sda5 
file system: ext3 
mount point: media/hda5 
size: 9.77G 
used: 307M
unused: 9.47G

Guys, by all means, I very appreciate your help and time to help me.  lets, see what is next... 

danial

---

### Post by forestpixie on 2008-05-13
Going by what you have as UUID for swap and ajgreeny post - you have these wrong, the one you have commented out is the one which is showing as current on an earlier post  - or has it changed again?

# UUID=39706b86-d13a-4b0c-8899-ef9c10b03fbc none swap sw 0 0
UUID=5ea03674-b869-4d27-9068-79af58a25326 none swap sw 0 0

Last year I used this to help me move /home 
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by danial-aalee on 2008-05-13
> **forestpixie said:**
> Going by what you have as UUID for swap and ajgreeny post - you have these wrong, the one you have commented out is the one which is showing as current on an earlier post - or has it changed again?
 
# UUID=39706b86-d13a-4b0c-8899-ef9c10b03fbc none swap sw 0 0
UUID=5ea03674-b869-4d27-9068-79af58a25326 none swap sw 0 0

 
Yes, it has changed.  I did reformat the swap partition (per AJGreeny instruction) and then I got new UUID, which is:
**5ea03674-b869-4d27-9068-79af58a25326**
 
This is the one in use as of now.  Line above which I commented out in /etc/fstab is the old UUID.
 
I will work on thee link you sent me later tonight.  and as always, I am very grateful for your help and time.
 
danial

---

### Post by forestpixie on 2008-05-13
Not really sure what's going on with your swap at all - sorry. 

It certainly looks like it should work as it is, I'm intrigued as to why you have references to hda* in fstab and fdisk reports sda* - I assume it's not important or someone would have said by now. I know that they were hda a while back.

But then also I don't know why system monitor reports different than top.


I do know that htop and top report memory in a slightly different way, htop appears to correspond to system monitor

---

### Post by danial-aalee on 2008-05-13
AJ,
 
Okay let me do some screenshots later tonight and I will attach those (later tonight after I figure out screen capture - I know I have seen a utility for that).  Hopefully, you or forestpixie will see what I am missing.
 
Thank you very much for everything you guys are doing...
danial

---

### Post by danial-aalee on 2008-05-14
Alright,
Here are two screen shots - before partition editor ran and after.  Name are self explanatory...  I tried to get results of **top** and **/etc/fstab** and **fdisk** -l while System Monitor (KDE4) in upper left corner.  

Also third snap is for my both hard drives in gparted and fdisk -l results together...

Smack me on my head where and what I am missing or what i am doing wrong here...

danial

---

### Post by forestpixie on 2008-05-14
I wonder whether you are trying to compare apples and oranges here - what does free -m report when the kde sys monitor says there is no swap left?

---

