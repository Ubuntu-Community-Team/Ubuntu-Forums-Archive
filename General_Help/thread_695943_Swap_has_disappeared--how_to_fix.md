---
title: "Swap has disappeared--how to fix?"
date: 2008-02-13
forum: General Help
---

### Post by bornagainpenguin on 2008-02-13
Hi everyone!

I'm trying to figure out how to get Ubuntu to start using my swap again...  I followed the guide listed [here](http://ubuntuforums.org/showthread.php?t=204069) but it didn't seem to do anything ;(

--bornagainpenguin

---

### Post by taurus on 2008-02-13
Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
free
```

---

### Post by bornagainpenguin on 2008-02-13
> **taurus said:**
> Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
free
```

Here you go....

```
bornagainpenguin@Inspiron5100:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ddaab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          97      779121   82  Linux swap / Solaris
/dev/sda2   *          98         951     6859755   83  Linux
/dev/sda3             952        1251     2409750   83  Linux
/dev/sda4            1252        4864    29021422+  83  Linux
bornagainpenguin@Inspiron5100:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=84585448-d905-4320-80b7-d72297888da4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=d500872f-9a99-492b-8c14-c5ec615fd026 /home           ext3    defaults        0       2
# /dev/sda4
UUID=4b244fb0-82df-4a1d-b799-22861b89c585 /home/mydocs    ext3    defaults        0       2
# /dev/sda1 swap swap defaults 0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
bornagainpenguin@Inspiron5100:~$ free
             total       used       free     shared    buffers     cached
Mem:        516436     366400     150036          0       9572     184172
-/+ buffers/cache:     172656     343780
Swap:            0          0          0
```

Thanks for replying!

--bornagainpenguin

---

### Post by taurus on 2008-02-13
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   none   swap   sw   0   0
```
Save it and close down gedit window.  Then, run

```
sudo mount -a
free
```

---

### Post by bornagainpenguin on 2008-02-13
Still no swap...

--bornagainpenguin

---

### Post by taurus on 2008-02-13
```
sudo mkswap /dev/sda1 
sudo swapon /dev/sda1
free
```

---

### Post by bornagainpenguin on 2008-02-13
> **taurus said:**
> ```
sudo mkswap /dev/sda1 
sudo swapon /dev/sda1
free
```

Okay this time was different!  I shut down the laptop after my last post and when it booted up I tried running the commands you told me ad got this result:

```
bornagainpenguin@Inspiron5100:~$ sudo mkswap /dev/sda1
[sudo] password for bornagainpenguin:
/dev/sda1: Device or resource busy
bornagainpenguin@Inspiron5100:~$ sudo swapon /dev/sda1
swapon: /dev/sda1: Device or resource busy
bornagainpenguin@Inspiron5100:~$ free
             total       used       free     shared    buffers     cached
Mem:        516436     369772     146664          0       9668     185296
-/+ buffers/cache:     174808     341628
Swap:       779112          0     779112
```

This time at least it's showing SOMETHING in the System monitor!

--bornagainpenguin

---

### Post by taurus on 2008-02-13
It just means that your swap partition is working so no need to do anything else.

---

### Post by bornagainpenguin on 2008-02-13
> **taurus said:**
> It just means that your swap partition is working so no need to do anything else.

Okay then... Thanks for the help...hopefully I'll remember all this if it ever happens again...

--bornagainpenguin

---

### Post by bimargulies on 2008-03-03
I followed the prescription, and got no effect.

bim-1330% sudo swapon -a
swapon: /dev/sda5: Invalid argument
bim-1330% sudo mount -a
bim-1330% sudo swapon -a
swapon: /dev/sda5: Invalid argument
bim-1330% free
             total       used       free     shared    buffers     cached
Mem:       3631000    2242888    1388112          0     550260     826648
-/+ buffers/cache:     865980    2765020
Swap:            0          0          0
bim-1330% sudo swapon -s
Filename                                Type            Size    Used    Priority
bim-1330%

---

### Post by bimargulies on 2008-03-03
I've figured this out. What happened to you is what happened to me: your swap partition header got hammered.

If you look at [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq), you will see a recipe for running mkswap to rewrite the header. **be sure to run this only on the swap partition from fdisk. Be sure that this partition does not overlap some other partition.**

Once you have re-headered your swap partition, it will get a new uuid. So you either have to change your fstab to use the dev pathname, or use the new uuid from the mkswap command.

---

