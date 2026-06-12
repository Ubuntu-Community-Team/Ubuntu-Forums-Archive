---
title: "Please Please Help me With LILO"
date: 2007-02-11
forum: General Help
---

### Post by hempa on 2007-02-11
Please help me installing LILO is my only hope to boot ubuntu. 
I have gotten to the point in in the installation of LILO were im typing the sudo liloconfig command in the terminal and then i get this message.

ubuntu@ubuntu:~$ sudo liloconfig
LILO, the LInux LOader, sets up your system to boot Linux directly
from your hard disk, without the need for a boot floppy.

    WARNING!
        Your /etc/fstab configuration file gives device unionfs as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle.

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/.
ubuntu@ubuntu:~$ /usr/share/doc/lilo/.

How can i go on from here? Please help me give me a thread advice anything! i have been trying to boot ubuntu for three days now.

---

### Post by koenn on 2007-02-11
Are you working of a LiveCD or something ?
And why are you using LiLo ?

---

### Post by llamakc on 2007-02-11
Sure, give us more information. 

1. Are you trying to install from a LiveCD? If so, have you mounted your hard drives or checked to see if they are mounted?

2. If you are using a LiveCD, give us the output of `sudo fdisk -l /dev/hda` (provided you have one hard disk in the machine and it is the primary master).

3. Once you have mounted /dev/hda, give us the output of `cat /path/to/hdaX/etc/fstab` [where X represents the partition on the disk and "/path/to/" represents the mounted path]

4. If you're not in a LiveCD, can you show us what your /etc/fstab looks like?

Last, why do you HAVE to install LiLo? Could not Grub work just fine? What has happened that created this situation?

---

### Post by hempa on 2007-02-11
> **koenn said:**
> Are you working of a LiveCD or something ?
And why are you using LiLo ?

yes i am working from a live cd but i have ubuntu installed on the harddrive but when i turn on the computer it just says loading grub in bios and then it freezes there. i have tried reinstalling grub repairing and all other options i could find in different threads everything seems to work out all right in the terminal but when i reboot without the live cd same thing, loading grub and it wont go on from there, i read about someone that also tried everything with grub and failed and then tried LILO and it worked fine, thought i would trie the same thing

---

### Post by llamakc on 2007-02-11
Okay, where did you read that? Share the link. Have you tried hitting the "escape" key to gain access to the GRUB menu, and trying an older kernel?

---

### Post by hempa on 2007-02-11
> **llamakc said:**
> Sure, give us more information. 

1. Are you trying to install from a LiveCD? If so, have you mounted your hard drives or checked to see if they are mounted?

2. If you are using a LiveCD, give us the output of `sudo fdisk -l /dev/hda` (provided you have one hard disk in the machine and it is the primary master).

3. Once you have mounted /dev/hda, give us the output of `cat /path/to/hdaX/etc/fstab` [where X represents the partition on the disk and "/path/to/" represents the mounted path]

4. If you're not in a LiveCD, can you show us what your /etc/fstab looks like?

Last, why do you HAVE to install LiLo? Could not Grub work just fine? What has happened that created this situation?

I really suck at this so i dont know if any of my harddrives is the primary master. i have two harddrives 160gig each and because i am a nut i have ubuntu installed on both of them. this is what happend when i typed: sudo fdisk -l /dev/hda

Disk /dev/hda doesn't contain a valid partition table
ubuntu@ubuntu:

this is what came up when i just typed: sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19452   156248158+   5  Extended
/dev/sda5   *           1          31      248944+  83  Linux
/dev/sda6              32       19452   155999151   8e  Linux LVM

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18695   150167556   83  Linux
/dev/sdb2           18696       19452     6080602+   5  Extended
/dev/sdb5           18696       19452     6080571   82  Linux swap / Solarisubuntu@ubuntu:~$

Please keep on helping and dont let me hang here alone i really suck at this but i am learning

---

### Post by hempa on 2007-02-11
here is the thread i followed [http://ubuntuforums.org/showthread.php?p=855069](http://ubuntuforums.org/showthread.php?p=855069)

---

### Post by llamakc on 2007-02-11
My bad. I forgot to mention that your drives may be /dev/sda instead of /dev/hda. I still make that mistake with my hardware.

So you have two hard drives and Ubuntu installed on both. Was that on purpose? Are they different versions? Do you want it installed on both of them?

Just as GRUB loads, hit the escape key. See if you can get the menu. If you can, arrow-down to an older kernel and try booting. 

PS: was the second install of Ubuntu done after it initially messed up?

---

### Post by hempa on 2007-02-11
i have not tried a older kernel if i am going to do yhat i need some help

---

### Post by llamakc on 2007-02-11
> **hempa said:**
> here is the thread i followed [http://ubuntuforums.org/showthread.php?p=855069](http://ubuntuforums.org/showthread.php?p=855069)

That person did not use LiLo from the LiveCD.

---

### Post by llamakc on 2007-02-11
> **hempa said:**
> i have not tried a older kernel if i am going to do yhat i need some help

Okay, I explained it but will do so again.

Reboot the computer. RIGHT when the grub prompt comes up at the bottom, please hit the escape key. You should have a menu now. Use the arrow keys to toggle down and select a kernel. Typically this will be two entries below the one on top.

---

### Post by hempa on 2007-02-11
> **llamakc said:**
> My bad. I forgot to mention that your drives may be /dev/sda instead of /dev/hda. I still make that mistake with my hardware.

So you have two hard drives and Ubuntu installed on both. Was that on purpose? Are they different versions? Do you want it installed on both of them?

Just as GRUB loads, hit the escape key. See if you can get the menu. If you can, arrow-down to an older kernel and try booting. 

PS: was the second install of Ubuntu done after it initially messed up?

ok the fast version of what heppend is, i had windows xpas OS and i wanted to try ubuntu so i installed it with the live cd on one of the harddrives when i rebooted i had the grub problem since i know nothing about this i thoght that maybe it was windows on the other harddrive that was messing things up so i installed ubuntu again on the other harddrive so now i have ubuntu on both but i cannot acces any of them i have tried lots of things to make grub work but nothing works. one of the threds i have followed is this one  [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by hempa on 2007-02-11
i tried to type the command you gave me earlier but used the letters sda insted of hda this is what i got hope its of help
Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18695   150167556   83  Linux
/dev/sdb2           18696       19452     6080602+   5  Extended
/dev/sdb5           18696       19452     6080571   82  Linux swap / Solarisubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       19452   156248158+   5  Extended
/dev/sda5   *           1          31      248944+  83  Linux
/dev/sda6              32       19452   155999151   8e  Linux LVM
ubuntu@ubuntu:~$

i am also going to try an older kernel soon

---

### Post by koenn on 2007-02-11
so it's basically 2 freshly installed ubuntu systems (on on each drive), and grub confused about it. Windows is wiped. 
If there's nothing else there, you have nothing left to lose - I'd say just wipe the drives and reinstall. 

lamakc, what do you think ?

---

### Post by llamakc on 2007-02-11
I completely agree. Make sure when the partitioner is run to be CERTAIN to format /dev/sda and /dev/sdb so that Grub doesn't get confused after the install again.

To do this choose manually edit partition table, 

[img]http://www.linuxlibrarian.org/files/Ubuntu/snap8.png[/img]

---

### Post by hempa on 2007-02-11
> **koenn said:**
> so it's basically 2 freshly installed ubuntu systems (on on each drive), and grub confused about it. Windows is wiped. 
If there's nothing else there, you have nothing left to lose - I'd say just wipe the drives and reinstall. 

lamakc, what do you think ?
thanks man i will try it as a last resort. how do i erase one of the harddrives (i am a total newbie)

---

### Post by hempa on 2007-02-11
> **llamakc said:**
> I completely agree. Make sure when the partitioner is run to be CERTAIN to format /dev/sda and /dev/sdb so that Grub doesn't get confused after the install again.

To do this choose manually edit partition table, 

[img]http://www.linuxlibrarian.org/files/Ubuntu/snap8.png[/img]

ok but i dont need ubuntu on both my drives can i erease one of the drives and keep the otherone with ubuntu or will grub still be confused??

---

### Post by koenn on 2007-02-11
Don't remember exactly. 
when the partitioner starts, choose "manualy ..." - as llamakc says.
then, either
- check "format" for every partition,
or 
- erase all partitions and make new ones.

Don't remember - llamakc is simulating it already so he can walk you through it i think

---

### Post by llamakc on 2007-02-11
> **koenn said:**
> Don't remember exactly. 
when the partitioner starts, choose "manualy ..." - as llamakc says.
then, either
- check "format" for every partition,
or 
- erase all partitions and make new ones.

Don't remember - llamakc is simulating it already so he can walk you through it i think

Do as koenn says. When you choose to manually edit the partition table, you get the partitioner. I "think" it has a dropdown menu (in upper right?) where you select which drive you want to edit. 

You want to format both drives completely, letting Ubuntu use /dev/sda to install to.

---

