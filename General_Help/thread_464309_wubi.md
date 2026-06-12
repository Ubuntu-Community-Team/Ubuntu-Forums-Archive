---
title: "wubi"
date: 2007-06-04
forum: General Help
---

### Post by ReaLitaliano on 2007-06-04
i installed ubuntu using wubi it was slow to boot but it worked four 2 days then when i restarted it so i can go back to use xp i got a black screen saying strike F1 to retry boot, F2 for setup utility. i tryed 2 fix it using super grub disk but got error 15 file not found.if i try to boot any OSs it says error on loading operating system. i dont care about ubuntu i just want windows 2 work right now.

---

### Post by ago on 2007-06-04
Did you hard reboot? Anyway your best shot is to use windows chkdsk & co (see windows recovery console) + you can use a live CD to access the partition and check if something is wrong.

---

### Post by ReaLitaliano on 2007-06-04
i cant boot from hard drive,how would i use chkdsk from the install cd? how would i use windows recovery console what command do i use i dont want lose any important data from my windows xp

---

### Post by ago on 2007-06-04
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

as mentioned you can also boot from a live CD to access the windows partition and copy the important data to some other device.

---

### Post by ReaLitaliano on 2007-06-04
ok using the live cd how can i copy the data?

---

### Post by ago on 2007-06-04
open the windows folder with the file browser (depending on the live CD you might have to mount the windows partitions manually, ask here if that's the case) then that works as any other file browser, attach another disk and copy it over.

---

### Post by ReaLitaliano on 2007-06-04
i cant because i dont see my hard drive and i tried to search it but nothing.

---

### Post by ago on 2007-06-04
are you booted with the live CD?

then open a shell and type

cat /proc/partitions

that lists available partitions (/dev/hda1 /dev/hda2...) , you can try to mount them with

sudo mkdir /media/p1
sudo mount /dev/XXX /media/p1

sudo mkdir /media/p1
sudo mount /dev/YYY /media/p1

replace XXX and YYY withe the entries from the cat command

---

### Post by ReaLitaliano on 2007-06-04
8     0   78125000 sda
   8    16    1000944 sdb
   8    17     996376 sdb1
   7     0     646072 loop0
ubuntu@ubuntu:~$ sudo mkdir /media/p1
mkdir: cannot create directory `/media/p1': File exists
ubuntu@ubuntu:~$ sudo moun /dev/sda/media/p1

---

### Post by ReaLitaliano on 2007-06-04
not working

---

### Post by ReaLitaliano on 2007-06-04
well thanks 4 helping

---

### Post by ago on 2007-06-04
> **ReaLitaliano said:**
> 8     0   78125000 sda
   8    16    1000944 sdb
   8    17     996376 sdb1
   7     0     646072 loop0
ubuntu@ubuntu:~$ sudo mkdir /media/p1
mkdir: cannot create directory `/media/p1': File exists
ubuntu@ubuntu:~$ sudo moun /dev/sda/media/p1

you only need to create p1 once

to mount

sudo mount /dev/sdb1 /media/p1

now hard disk 2 can be accessed from /media/p1

I see you have 2 disks but there does not seem to be any partition in disk 1. Do you have 2 hard disks? Is disk 1 the one containing windows? If so the MBR is probably missing.

---

### Post by ReaLitaliano on 2007-06-05
i only have 1 hard drive

---

### Post by ago on 2007-06-05
1GB usb key?

anyway there is no partition in first HD

---

### Post by ReaLitaliano on 2007-06-05
yes usb drive
no partition on the second ok but is there a way to fix it

---

### Post by ago on 2007-06-05
[http://www.linuxforums.org/forum/167833-post3.html](http://www.linuxforums.org/forum/167833-post3.html)

---

### Post by ReaLitaliano on 2007-06-05
ok got to try but i dont know my admin password

---

### Post by ReaLitaliano on 2007-06-05
will i still have my files?

---

### Post by ago on 2007-06-05
If it's an mbr/partition table probably yes.

---

### Post by ReaLitaliano on 2007-06-05
i tried fixmbr and nothing

---

