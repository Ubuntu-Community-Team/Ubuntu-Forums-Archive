---
title: "help reinstall  ubuntu"
date: 2007-01-10
forum: General Help
---

### Post by abhishekp on 2007-01-10
Hello I am  still trying to get back my linux. I resolved the grub problem by reinstalling it. 
see [http://ubuntuforums.org/showthread.php?t=326929]("http://ubuntuforums.org/showthread.php?t=326929")
Now  when i try to boot the ubuntu splash screen comes up and starts loading. After loading 1 or 2 modules it stops and a message appears on the screen saying cannot read /etc/fstab/ no such file or folder. Is there any way I can get it back into booting to the same state as it was before? Is it possible to reinstal ubuntu without disturbing anything else on the drive including settings?

---

### Post by bodhi.zazen on 2007-01-10
It looks like you lost your Ubuntu install.

Can we look at the partition ?

Boot to the live CD and mount the Ubuntu root partition to /media/ubuntu.

What is in /media/ubuntu and /media/ubuntu/etc

```
sudo mkdir /media/ubuntu
sudo mount /dev/hdxx /media/ubuntu
ls /media/ubuntu
cat /media/ubuntu/etc/fstab
```Where /dev/hdxx is your ubuntu root partition (?/dev/hda2)

---

### Post by az on 2007-01-10
The problem was not only grub but that you changed your partition ordering.

Ubuntu will eventually handle this better.  For now, you need to boot th elive cd and edit your fstab so that your / directory is mounted in the proper place.  You need to tell grub that, too.  I think the root line is not pointing to the right partition.

---

### Post by abhishekp on 2007-01-11
Yes I can look at the partition, but there is no /etc/fstab.

---

### Post by abhishekp on 2007-01-11
How do  i find  the  right  partition number?

---

### Post by bodhi.zazen on 2007-01-11
List your partitions:

```
sudo fdisk -l
```

Mount them and look for your root partition (manually)

---

### Post by abhishekp on 2007-01-13
Thank you all for your help, I was able to boot up linux once again. Now there is another problem, it is running very slow and system hangs often. Is it the swap partition? cause I didn't change it in fstab. Should I change it?

---

### Post by bodhi.zazen on 2007-01-13
Glad to hear you are up an running ....

sorry to hear of your continued woes ....

How much RAM do you have ?

What are you running when your system hangs ?

---

