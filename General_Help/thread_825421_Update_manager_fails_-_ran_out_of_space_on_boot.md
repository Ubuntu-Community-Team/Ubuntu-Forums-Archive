---
title: "Update manager fails - ran out of space on /boot"
date: 2008-06-11
forum: General Help
---

### Post by theedudenator on 2008-06-11
I am not sure why, but it is downloading and trying to update from my /boot 
This is a small partition just for GRUB boot manager.

How can I change the directory where the update files are installed?

I tried to delete some of the old files from boot, but it says I do not have permission.

Any suggestions?

---

### Post by mikewhatever on 2008-06-11
Take a look at your /boot partition with <ls /boot>. The kernel is also there, and that's what takes up space and updates. If you wanted a dedicated GRUB partition, it should never have been mounted under /boot. If there are older kernels you don't use, uninstall them from Synaptic, or else, make /boot bigger with gparted cd.

---

### Post by Abetorius on 2008-06-11
```
sudo nautilus
```
will open nautilus with permissions to remove every file you want. Be careful with that.

---

### Post by theedudenator on 2008-06-11
I thought /boot was for GRUB.

I made it the 1st partition as 40meg.

I can resize it.  4gig should be good for now??

---

### Post by plucky on 2008-06-11
> 4gig should be good for now?? 


Way too large,the whole system can be installed in 4G,
I would go for 100M for /boot,if you really need a separate boot partition.
You can also clear out some of the old kernels using synaptic package manager,but I would keep at least one older working kernel,just in case a kernel update causes the system to break.


Good Luck

---

### Post by armandop on 2008-06-11
I'm having the same problem. Got a new 500gb drive and created a 64MB boot partition installed grub on it and mounted it as /boot. After 3 days of Ubuntu updates it is now full. Unfortunately I cannot extend it as there's another partition right next to it.

I was trying to have a boot partition where I could have grub load other OS from. 

I dont understand how a boot partition should work. Where did I go wrong ?

---

### Post by Golem XIV on 2008-06-11
There were several kernel updates since Hardy came out (16, 17, 18 and now 19).  That's probably the reason why /boot is full.  Get rid of the old kernel(s)

---

### Post by plucky on 2008-06-11
Let us see what your /boot partition holds.


```
ls -l /boot 
``` That is lowercase L not a 1.



Your boot partition contains the kernel image and other files required to boot.Every time a new kernel is released,it adds to the boot partition.It is good practice to keep at least one spare working kernel in case the latest kernel has any problems.


To remove earlier kernels use ```
sudo dpkg purge linux-image-2.6.24-16-generic
``` substitute the value in the linux-image part for the kernels you want to remove.



Good Luck

---

### Post by meierfra. on 2008-06-11
armandop:  You created a /boot partition instead of a grub partition. If you want  turn your /boot partition into a grub partition you need to

1)  Change #groot (hd?,?) in /boot/grub/menu.lst so that it points to your ubuntu partition and not to your /boot partition.  Then  type "sudo update-grub" in a terminal.

2)   unmount you /boot partition.

3)  mount your /boot partition to /media/tmp

4)  Move the   files in /media/tmp  to /boot (but to not move  the folder grub or any of the files in grub)

5)  remove the line "/dev/..  /boot ......" from /etc/fstab


For more detailed help, post the output of
```
sudo fdisk -l
```

and 

```
cat /boot/grub/menu.lst
```

(Your other options are :  
Increase the size of the /boot partition.  
Remove you old kernel via synaptic.)

You might also want to click on drs305 in my signature.

---

### Post by adrian15 on 2008-06-12
> **meierfra. said:**
> armandop:  You created a /boot partition instead of a grub partition. If you want  turn your /boot partition into a grub partition you need to

Your instructions are meant to create to incorporate the /boot folder into the / partition (**not a grub partition !**). Is it like that?

By the way I don't see what's the problem on having a /boot partition. The problem is synaptic (or apt-get, or the kernel update post-inst script) not taking care about /boot free space and removing actually old kernels.

adrian15

---

### Post by meierfra. on 2008-06-12
> Your instructions are meant to create to incorporate the /boot folder into the / partition (not a grub partition !). Is it like that?

My instruction incorporate MOST of the /boot folder into the / partition. But I leave the grub folder on the /boot partition   and whereby turning the /boot partition into a /grub partition.


> removing actually old kernels.

There are always some people having problems with the new kernel. Automatically deleting the old kernels, would (in my opinion) cause more problems than it would solve.

---

### Post by adrian15 on 2008-06-12
> **meierfra. said:**
> My instruction incorporate MOST of the /boot folder into the / partition. But I leave the grub folder on the /boot partition   and whereby turning the /boot partition into a /grub partition.

And? Why is it useful to have a /grub partition? The /boot partition is usually used to avoid the [error 18 problem](http://www.supergrubdisk.org/wiki/GrubError18). This problem not only occurs when Grub is trying to find its own files but also when it tries to load the kernel because it needs also to find the kernel!

I don't see the point on having a /grub partition. Can you please elaborate on this subject? Thank you.

> **meierfra. said:**
> 
There are always some people having problems with the new kernel. Automatically deleting the old kernels, would (in my opinion) cause more problems than it would solve.

I am sorry. When I said **actually old** I meant that for example: There is a maximum of four kernels and when the fifth kernel is being added then the first kernel is removed (if the user agrees of course).

adrian15

---

### Post by meierfra. on 2008-06-12
> I don't see the point on having a /grub partition. Can you please elaborate on this subject? Thank you.

A grub partition is usefull if you play around with lots of different distros:

1)  It keeps the Grub Menu tighty. I don't put any of the recovery options  and alternate Kernel on my grub menu. Instead I just chainload the Grub menu for each OS. So my main grub menu just has one title per OS.

2)  One never has to worry about  accidentally deleting the Main Grub menu   when one OS is replaced by another (and believe me, I have actually done that before I had a dedicated Grub partition) 

But to be honest, for the average user a dedicated grub partition is pretty much useless. 



> is a maximum of four kernels and when the fifth kernel is being added then the first kernel is removed (

Well what happens if all of the four newest kernel don't work? Ubuntu 8.04 had three different kernel in the last 2months, with the fourthed one coming soon. So this could easily happen.

Also have I have seen various cases where the boot partition was already full after the third kernel (o.k. that's their own fault for creating a to small boot partition, but it still happens)

---

### Post by adrian15 on 2008-06-12
> **meierfra. said:**
> A grub partition is usefull if you play around with lots of different distros:

1)  It keeps the Grub Menu tighty. I don't put any of the recovery options  and alternate Kernel on my grub menu. Instead I just chainload the Grub menu for each OS. So my main grub menu just has one title per OS.

I know. :) I use one grub partition myself. However I create a new grub partition. I think you confused me. I mean. If I was me who was explaining your procedure I would have said: 

1) Incorporate /boot (with the grub files! **By the way... why did not include the grub folder?... Are you going to generate it later at hand?**) to root. 

2) Create the new grub partition by shrinking the Linux one.

and not saying "Converting /boot partition into /grub partition".

> **meierfra. said:**
> 
2)  One never has to worry about  accidentally deleting the Main Grub menu   when one OS is replaced by another (and believe me, I have actually done that before I had a dedicated Grub partition) 

That's also true.
> **meierfra. said:**
> 
But to be honest, for the average user a dedicated grub partition is pretty much useless. 

Humm... it depends on the partition layout and bios limit.

That's how I have set up my system but if I had to re set up it I would try to make a 300 MB /boot partition to put there all the distribution kernels so that I do not have any problem with the error 18 problem.

Please check: [Error 18 problem](http://www.supergrubdisk.org/wiki/GrubError18).



> **meierfra. said:**
> 
Well what happens if all of the four newest kernel don't work? Ubuntu 8.04 had three different kernel in the last 2months, with the fourthed one coming soon. So this could easily happen.


You are right. That's why the user should be asked about it... the problem is that most users might not be aware of it. So there should be some kind of graphical application that tries a new kernel boot, if it does work it asks for the user for verifying hardware support and asks if the new kernel should stay there or not. Quite complicated!

> **meierfra. said:**
> 
Also have I have seen various cases where the boot partition was already full after the third kernel (o.k. that's their on fault for creating a two small boot partition, but it still happens)

User's fault or post-inst script fault on not considering situations where only one kernel and one initrd can be in a /boot folder so that another temporary location should be used to swap old and new kernels?

adrian15

---

### Post by meierfra. on 2008-06-12
> I think you confused me. I mean. If I was me who was explaining your procedure I would have said

But you are explaining a completely different procedure. So let me try to explain it again. (My procedure is not about creating a grub partition, but about turning a boot partition into a grub partition)

At the beginning  the OP has two partition: say sda1 and sda2

sda1 in mounted at /boot
sda2 is mounted at /

So sda 1 contains the kernel's, initrd's and the grub folder.

After my procedure:

sda 1 is mounted nowhere.
sda 2 is mounted at /

the grub folder is still in sda1. But kernel's and initrd's are on sda2 in the boot folder.

I did not resize any partition and I did not create any new partitions.

sda1 used to be a boot partition, but now is dedicated grub partition. The only contents of sda1 is the grub folder.


> Please check: Error 18 problem.

 Yes,  a /boot partition can prevent Error 18. But I was talking about a /grub partition.

---

### Post by adrian15 on 2008-06-12
> **meierfra. said:**
> 
 Yes,  a /boot partition can prevent Error 18. But I was talking about a /grub partition.

Ok.

adrian15

---

### Post by outlikeashoe on 2008-10-30
Here the same problem: I have (in this order on the same drive):
- two windows partition (ntfs)
- extended partition with:
--- / (ext3)
--- /home (reiserfs)
--- swap partion (512 mb)
--- /boot partition (64 mb) at the end of the drive
--- fat32 partition (5 gb) to share with windows

The error it's not enought free space in /boot, actually I have only kernel 2.6.24-21, I've already removed the previous versions.

What can I do?
Last time I worked with partitions, I had to reinstall the OS... please answer clearly...

---

### Post by plucky on 2008-10-30
> **outlikeashoe said:**
> Here the same problem: I have (in this order on the same drive):
- two windows partition (ntfs)
- extended partition with:
--- / (ext3)
--- /home (reiserfs)
--- swap partion (512 mb)
--- /boot partition (64 mb) at the end of the drive
--- fat32 partition (5 gb) to share with windows

The error it's not enought free space in /boot, actually I have only kernel 2.6.24-21, I've already removed the previous versions.

What can I do?
Last time I worked with partitions, I had to reinstall the OS... please answer clearly...


Open a terminal and ```
cd /boot
ls -l
df -h
``` (lowercase L not a 1) will show the files in the /boot partition.(Post output of commands)

> I've already removed the previous versions.

Did you use synaptic to remove the previous linux images,or did you just remove them from **menu.lst**.

---

### Post by outlikeashoe on 2008-10-30
$> ls -l
totale 18775
-rw-r--r-- 1 root root  420395 2008-10-22 03:49 abi-2.6.24-21-generic
-rw-r--r-- 1 root root   74177 2008-10-22 03:49 config-2.6.24-21-generic
drwxr-xr-x 2 root root    1024 2008-10-28 19:24 grub
-rw-r--r-- 1 root root 7733856 2008-10-28 12:19 initrd.img-2.6.24-21-generic
-rw-r--r-- 1 root root 7734199 2008-10-16 16:36 initrd.img-2.6.24-21-generic.bak
drwxr-xr-x 2 root root   12288 2008-04-29 21:48 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 13:03 memtest86+.bin
-rw-r--r-- 1 root root 1153201 2008-10-22 03:49 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1905688 2008-10-22 03:49 vmlinuz-2.6.24-21-generic

$> df -h
File system            Dimens. Usati Disp. Uso% Montato su
/dev/sda9              14G  7,4G  5,1G  60% /
varrun               1007M  112K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M   72K 1007M   1% /dev
devshm               1007M  408K 1007M   1% /dev/shm
lrm                  1007M   44M  963M   5% /lib/modules/2.6.24-21-generic/volatile
/dev/sda6              59M   34M   23M  60% /boot
/dev/sda8              15G  8,5G  5,6G  61% /home
/dev/sda2              74G   55G   19G  75% /windati
/dev/sda1              80G   65G   16G  81% /windows
/dev/sda5             5,3G  169M  5,2G   4% /winfat
gvfs-fuse-daemon       14G  7,4G  5,1G  60% /home/eros/.gvfs

I removed the previous versions with `sudo rm /boot/*$oldkernelversion*`
and updated the menu.lst manually.

Thanks for the quick answer.

---

### Post by plucky on 2008-10-30
> /dev/sda6 59M 34M 23M 60% /boot

The numbers do not add up.It says you have 34M used but your files only add up to about 20M.I am wondering if you have some files stuck in a hidden root trash folder.


See this [thread](http://ubuntuforums.org/showthread.php?t=898573) on how to clear out your trash.


Good Luck

---

### Post by outlikeashoe on 2008-10-30
Done.. you're right there was an hidden Trash folder.. deleted the files but I still have problems.
The updater tell me that I need 35 Mb more, but I only have 18.4 Mb used.
Thanks again.

---

### Post by plucky on 2008-10-30
> **outlikeashoe said:**
> Done.. you're right there was an hidden Trash folder.. deleted the files but I still have problems.
The updater tell me that I need 35 Mb more, but I only have 18.4 Mb used.
Thanks again.

Sorry I don't understand.

If you have cleared out the trash from that partition,you should have about 40M of unused space. What does ```
df -h
``` give you.

What are you updating? 
Does it include a kernel update?
Are you trying to do a distribution upgrade to Intrepid?

> /dev/sda5 5,3G 169M 5,2G 4% /winfat

Perhaps you can resize the /winfat partition and add the space to the /boot partition using the partition editor on the Live CD

---

### Post by outlikeashoe on 2008-10-30
Yes, I'm upgrading to Intrepid, it requires 75 Mb in /boot (?? 75Mb for a kernel??).
If the safest way to update is to resize the other partition, I'll try this way.
Thanks for your help.

---

### Post by outlikeashoe on 2008-11-01
I used Gparted:
- removed the /winfat partition,
- expanded the /boot one
- re-created the vfat partition

Reboot:
-> Grub: Error 17

What's wrong? I realize that some of the /dev/sda# changes number: before gparted, the /boot partition was /dev/sda6, now it's /dev/sda5 and the old /winfat was sda5, now it's sda9.

I can't boot without a live cd, that's a very noisy problem.

---

### Post by outlikeashoe on 2008-11-02
Seems that I've solved the problem:
from the live cd:
$> sudo grub
$> root (hd0,4=
$> setup (hd0)

Reboot:
- Grub loaded, choose the OS from the list
- error 17
- edited the boot configuration, setting root to hd0,4

Bye!

---

### Post by icc97 on 2011-03-21
> **plucky said:**
> Your boot partition contains the kernel image and other files required to boot.Every time a new kernel is released,it adds to the boot partition.It is good practice to keep at least one spare working kernel in case the latest kernel has any problems.


To remove earlier kernels use ```
sudo dpkg purge linux-image-2.6.24-16-generic
``` substitute the value in the linux-image part for the kernels you want to remove.



Good Luck

Thanks @plucky, the purging of old kernels helped me clear up some space.  Your code was slightly incorrect though, for me it need to be: ```
sudo dpkg --purge linux-image-2.6.35-24-generic-pae
``` (I'm using ubuntu 10.10 (maverick))

---

