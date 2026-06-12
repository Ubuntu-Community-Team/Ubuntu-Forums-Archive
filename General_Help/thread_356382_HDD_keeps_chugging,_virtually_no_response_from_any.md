---
title: "HDD keeps chugging, virtually no response from anything!!! [Resolved]"
date: 2007-02-08
forum: General Help
---

### Post by mistafeesh on 2007-02-08
Hi, I'm a bit of an ubuntu noob, so I'm sorry if this is already fixed somewhere.
I'm using the 'edgy' release, which I've had on my laptop (a dell latitude) for a little while with not many problems. But suddenly everything has become unresponsive to the extreme. I move my finger on the trackpad and the cursor takes a while to respond - I try to open a openoffice file, and I can go away, make a cup of tea and come back before it's opened!

The hdd just keeps chugging away as if it's opening/writing files. 


any ideas???

PS, I've restarted etc several times, and also tried quitting X by hitting ctrl alt f1, but even with no x it's still incredibly unresponsive... eg, I've tried logging in with no x and it takes ages to even ask for the password!

---

### Post by taurus on 2007-02-08
How much RAM and swap space do you have on the machine?  Open a terminal and paste these outputs here.

```
free
top
```

---

### Post by mistafeesh on 2007-02-10
Thanks.

I can't actually get a browser open on the laptop at the moment, so it took a while to get the network on the laptop enough to copy a text file across. It would have probably been easier to just type it out!!!

Anyhow, here goes - 

free:
"total       used       free     shared    buffers     cached
Mem:        126208     121716       4492          0        108      29420
-/+ buffers/cache:      92188      34020
Swap:            0          0          0'

top:
"top - 15:22:02 up  1:38,  2 users,  load average: 0.09, 0.03, 0.07
Tasks:  77 total,   1 running,  76 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.0%us,  0.7%sy,  0.0%ni, 96.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    126208k total,   122596k used,     3612k free,      160k buffers
Swap:        0k total,        0k used,        0k free,    32036k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3846 root      15   0 23976 8760 2092 S  2.0  6.9   1:00.06 Xorg               
 4971 dan       16   0  2244  656  388 R  1.0  0.5   0:40.46 top                
 4640 dan       16   0 64352  10m 2896 S  0.3  8.2   0:10.76 gnome-panel        
 4665 dan       15   0 71248 7692 2140 S  0.3  6.1   0:34.16 gnome-terminal     
    1 root      17   0  1632  140   48 S  0.0  0.1   0:04.61 init               
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0        
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 events/0           
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.03 khelper            
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread            
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.86 kblockd/0          
   27 root      10  -5     0    0    0 S  0.0  0.0   0:00.06 kseriod            
   69 root      15   0     0    0    0 S  0.0  0.0   0:00.11 pdflush            
   70 root      15   0     0    0    0 S  0.0  0.0   0:00.13 pdflush            
   71 root      15   0     0    0    0 S  0.0  0.0   0:03.29 kswapd0            
   72 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0              
   76 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kpnpbiosd"


Hopefully that means more to you than it does to me!!

Cheers,

Dan

---

### Post by taurus on 2007-02-10
Somehow you don't have swap partition activated.  What does your /etc/fstab look like and the output of this command from a terminal?

```
cat /etc/fstab
sudo fdisk -l
```

---

### Post by mistafeesh on 2007-02-10
Okay,

here goes:

```
dan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=f409a04f-5e0c-4571-ac50-54f28e4fb774 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=47f41b60-06ba-414b-a07f-c552be836036 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
dan@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 10.0 GB, 10056130560 bytes
255 heads, 63 sectors/track, 1222 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1168     9381928+  83  Linux
/dev/hda2            1169        1222      433755    5  Extended
/dev/hda5            1169        1222      433723+  82  Linux swap / Solaris
dan@ubuntu:~$ 
dan@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=f409a04f-5e0c-4571-ac50-54f28e4fb774 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=47f41b60-06ba-414b-a07f-c552be836036 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
dan@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 10.0 GB, 10056130560 bytes
255 heads, 63 sectors/track, 1222 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1168     9381928+  83  Linux
/dev/hda2            1169        1222      433755    5  Extended
/dev/hda5            1169        1222      433723+  82  Linux swap / Solaris
dan@ubuntu:~$ 
```

thanks!!

---

### Post by sdide on 2007-02-10
hey,

try doing a (as root)
```
$ swapon -a
```

and then do a ```
free
``` after that. and check the swap.

---

### Post by Ptero-4 on 2007-02-10
Mista. You seem to have a swap partition. Try using this command:
```
sudo swapon /dev/hda5
```

And tell us what happens.

---

### Post by mistafeesh on 2007-02-10
Hi,

Both of those suggestions come up with "swapon: /dev/(disk name here): Invalid argument"

not sure what to do next. I'm trying to install gparted to see if I can get that to enable the swap, but I think it'll take a while!

---

### Post by sdide on 2007-02-10
Hey, 

Somehow it seems, that swapon can't recognize /dev/hda5 as a swap partition,
Can you try to remove it and then recreate it with fdisk (or gparted)
and then try "swapon -a" again.

---

### Post by taurus on 2007-02-10
```
sudo mkswap /dev/hda5
sudo swapon /dev/hda5
```
Now, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=47f41b60-06ba-414b-a07f-c552be836036 none swap sw 0 0
```
with this line.

```
/dev/hda5  none  swap  sw  0  0
```
Reboot and see what happens with the **free** command.

---

### Post by mistafeesh on 2007-02-11
yep!! That's better....

Phew! I'm glad it wasn't anything too drastic. If that was windoze or even OSX I might have had to re-install the lot!


Thanks very much guys 'n' gals!

PS am I supposed to mark this as "answered" somewhere?

---

