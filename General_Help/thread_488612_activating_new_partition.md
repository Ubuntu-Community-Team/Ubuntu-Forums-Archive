---
title: "activating new partition"
date: 2007-06-30
forum: General Help
---

### Post by bmorency on 2007-06-30
Hi,

I just created a new partition from some free space I had on a hard drive using the fdisk program in linux. It has been added as /dev/hdb6.  I tried to use mkfs to make the file system but I get the following error:

"Could not stat /dev/hdb6 --- No such file or directory

The device apparently does not exist; did you specify it correctly?"

I know I could reboot and it will be created by itself, but is there anyway to do it myself without rebooting? I am trying to learn more how things are actually done.

Thanks for any help.

---

### Post by jimbob on 2007-06-30
You need to mount it first then you can create file systems.

sudo mount /dev/hdb6 /mnt
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by bmorency on 2007-06-30
> **jimbob said:**
> You need to mount it first then you can create file systems.

sudo mount /dev/hdb6 /mnt
&#65279;

it will not let me mount it because it says that device does not exist. is there a way to make the system re detect all the devices and make a dev entry in the /dev folder without rebooting?

---

### Post by jimbob on 2007-06-30
Let us see the output of *[COLOR="Blue"]sudo fdisk -l[/COLOR]*

(That's a lower case "L")
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by bmorency on 2007-06-30
> **jimbob said:**
> Let us see the output of *[COLOR="Blue"]sudo fdisk -l[/COLOR]*

(That's a lower case "L")

when I do that I get this:

Disk /dev/hdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        6567    52749396    7  HPFS/NTFS
/dev/hdb2            6568       24321   142609005    5  Extended
/dev/hdb5            6568       12647    48837568+  83  Linux
/dev/hdb6           12648       18727    48837568+  83  Linux

when I do "ls /dev/hdb6" it says:

ls: /dev/hdb6: No such file or directory

what program creates the entries in the /dev folder?

---

### Post by jimbob on 2007-06-30
Do  you have Gparted installed?   *[COLOR="Blue"]apt-get install gparted[/COLOR]*

Does it see /dev/hdb6 as being a normal linux partition?  What type does it show?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by bmorency on 2007-06-30
Ok I recreated the partition it seems the only way to be able to use it is to reboot. After I exit fdisk it tells me to reboot so the kernel can use the new partition table. I must have missed that.

thanks for everyone's help.

---

