---
title: "How to Tell Ubuntu of new /home location"
date: 2007-06-24
forum: General Help
---

### Post by strange_cathect on 2007-06-24
Hello,

I used this [guide]("http://www.psychocats.net/ubuntu/separatehome") at [www.psychocats.net](www.psychocats.net) to create a separate partition for my **/home** folder.  I was successful in creating the new partition and in copying **/home** there.  So far so good.

However, during the process ubuntu has now lost the location of the home folder.  At login I am told that home folder is not where I have specified.

My question: how can I tell Ubuntu where to find /home?  I know that it exists at the volume: **/dev/sda4**

(I'm typing this on a live CD and will wait to see if anyone can offer any assistance)  

Thank you!

---

### Post by r0ck80y on 2007-06-24
Maybe the /home location is not mentioned in /etc/fstab file
Is there a line similar to this:```

/dev/sda4   /home   ext3   defaults   0  0 
``` ?

---

### Post by strange_cathect on 2007-06-24
I am currently running a live cd.  How can I open the grub file to check it?

Thanks for helping!

---

### Post by r0ck80y on 2007-06-24
open terminal. Type:```

sudo su
```
This makes you the live-CD root. Then mount the partition where you have stored linux i.e the / mount point. Say if that partition is /dev/sda2:```

mount /dev/sda2 /mnt 
cd /mnt/boot/grub
vi menu.lst
```
Lookup that entry here. You can post the grub file here if you want

---

### Post by strange_cathect on 2007-06-24
Something is missing here.  Commands not working.
> 
ubuntu@ubuntu:~$ sudo su

root@ubuntu:/home/ubuntu# mount /dev/sda2

mount: /dev/sda2 already mounted or /media/disk-3 busy

mount: according to mtab, /dev/sda2 is already mounted on /media/disk-3

root@ubuntu:/home/ubuntu# cd /mnt/boot/grub

bash: cd: /mnt/boot/grub: No such file or directory

---

### Post by r0ck80y on 2007-06-24
Check the commands again. Its "mount /dev/sda2 /mnt" You missed out the "/mnt" part :)

Also, is /dev/sda2 the partition where your / is mounted?? replace sda2 with the partition where your linux is stored. If still confused, then type this and post the output:```

fdisk /dev/sda 
```

---

### Post by strange_cathect on 2007-06-24
Aha.  Thanks...missed that.

I don't see any reference to /home in the grub menu.

But do you mean fstab?

---

### Post by r0ck80y on 2007-06-24
Ahh sorry..that was fstab not grub file :P
Go to /etc/fstab and check if that line is there ( Just edited that earlier post )

---

### Post by L8erG8er on 2007-06-24
r0ck80y,

I have a similar issue.  I have two hard drives in my machine, and I would like to make the second drive my /home partition.  (I went by the guided partitioning when I installed 7.04, and did not make a separate /home, oops).

Will that line in fstab work for me also?  Thanks.

---

