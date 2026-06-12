---
title: "/boot contains all of /"
date: 2006-11-16
forum: General Help
---

### Post by darknexus on 2006-11-16
Hello, kind of a strange problem here. Is /boot supposed to contain all of /? Recently when trying to compile an alsa module i got an error about System.map not being found. A quick gander in /boot revealed a full / contained within. Heres a little better explination of what i mean.

drknexus@ubuntu:~$ ls /boot
System.map-2.6.17-10-generic  initrd                        mnt   sys
bin                           initrd.img                    opt   tmp
boot                          initrd.img-2.6.17-10-generic  proc  usr
dev                           lib                           root  var
etc                           media                         sbin  vmlinuz
home                          memtest86+.bin                srv

drknexus@ubuntu:~$ ls /boot/boot
System.map-2.6.17-10-generic  initrd.img-2.6.17-10-generic
abi-2.6.17-10-generic         memtest86+.bin
config-2.6.17-10-generic      vmlinuz-2.6.17-10-generic
grub

Furthur examination reveals that the directories and files contained within /boot are identical to thoose contained on /. This is comming from a fresh install of ubuntu using the fakeraid howto. Anywho just wondering if this was indeed a problem or is it something i should not worry about. Thanks for any help ahead of time.

---

### Post by taurus on 2006-11-16
It should be the other way around, /boot is under /!  When you first installed Ubuntu, it will ask you where to mount your root partition so you have to pick /.  And if you have another partition for /boot, then you just mount it as /boot!  So, you need at least /...

---

### Post by darknexus on 2006-11-16
Thanks for reply, ill try to explain a bit better. There is indeed a /boot under /, but there is also /boot/boot as well as /boot/etc, /boot/bin, /boot/sbin etc... My partitions are as follows: 


                   Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_fhiadaea1               1         107      859446   82  Linux swap / Solaris
/dev/mapper/pdc_fhiadaea2           55704       60802    40957717+   5  Extended
/dev/mapper/pdc_fhiadaea3            2044       55703   431023950    7  HPFS/NTFS
/dev/mapper/pdc_fhiadaea4             108        2043    15550920   83  Linux
/dev/mapper/pdc_fhiadaea5   *       55704       60591    39262828+  83  Linux
/dev/mapper/pdc_fhiadaea6           60592       60802     1694826   82  Linux swap / Solaris

/pdc*5 has / and /boot , the rest except for /pdc*6 swap are not used under ubuntu

So i guess what I am trying to say is that i do indeed have a root partition with everything in it, its just that /boot for some reason contains the same. Thnx again for any help.

---

### Post by ciscosurfer on 2006-11-16
> **darknexus said:**
> Thanks for reply, ill try to explain a bit better. There is indeed a /boot under /, but there is also /boot/boot as well as /boot/etc, /boot/bin, /boot/sbin etc... My partitions are as follows: 


                   Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_fhiadaea1               1         107      859446   82  Linux swap / Solaris
/dev/mapper/pdc_fhiadaea2           55704       60802    40957717+   5  Extended
/dev/mapper/pdc_fhiadaea3            2044       55703   431023950    7  HPFS/NTFS
/dev/mapper/pdc_fhiadaea4             108        2043    15550920   83  Linux
/dev/mapper/pdc_fhiadaea5   *       55704       60591    39262828+  83  Linux
/dev/mapper/pdc_fhiadaea6           60592       60802     1694826   82  Linux swap / Solaris

/pdc*5 has / and /boot , the rest except for /pdc*6 swap are not used under ubuntu

So i guess what I am trying to say is that i do indeed have a root partition with everything in it, its just that /boot for some reason contains the same. Thnx again for any help.You don't want that kind of setup.  You want a root directory -- / -- and you want a boot directory under root -- /boot -- you don't want another full root directory under /boot -- that will get quite confusing and you will certainly experience issues. 
So, to recap, you need:
/
/boot
and the /boot should be under /
...and /root is the root users home directory (not to confuse you).
And you /boot directory CAN be placed into it's own partition as well.

---

### Post by darknexus on 2006-11-16
Wow that was an uber fast reply. My question is now, should i reinstall Ubuntu or is there a way to fix this without being too difficult? Everything seems to be working corecly so far but I would much rather have Ubuntu set up correctly to begin with to avoid problems down the road.

---

### Post by ciscosurfer on 2006-11-16
Backup the data you want to keep and then do a fresh install with the points we've made above in mind.  

Good Luck!

---

### Post by taurus on 2006-11-16
If you only have to partitions for Linux, then mount the first one to / and use the second one as swap...  That's all you need.

---

### Post by mayonaise15 on 2006-11-16
Could it be that they are just symbolic links?

---

### Post by ciscosurfer on 2006-11-16
> **taurus said:**
> If you only have to partitions for Linux, then mount the first one to / and use the second one as swap...  That's all you need.It's so much better to start fresh.

---

### Post by taurus on 2006-11-16
> **ciscosurfer said:**
> It's so much better to start fresh.
That's what I meant to mount the first one on / and use the second one (smaller) for swap when he/she installs it from fresh.  ;)

---

### Post by ciscosurfer on 2006-11-16
> **taurus said:**
> That's what I meant to mount the first one on / and use the second one (smaller) for swap when he/she installs it from fresh.  ;)Ah.  Got it. 8)

---

