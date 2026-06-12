---
title: "'Not enough room on disk' error while downloading"
date: 2014-05-17
forum: General Help
---

### Post by nisargshah on 2014-05-17
I use Ubuntu GNOME 13.10 32-bit as a standalone OS on my laptop. Whenever I try to download something using Firefox, I get the following popup -
[IMG]http://i.imgur.com/Fe1dvgu.png?1[/IMG]
I looked up on many forums and it seems this is a common error but I could find no results that were similar to mine. Here's my *df -h* output -
```
nisarg@nisarg-ThinkPad-T61:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   17G  940M  95% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            976M  4.0K  976M   1% /dev
tmpfs           198M  1.2M  197M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            988M  276K  988M   1% /run/shm
none            100M   40K  100M   1% /run/user
/dev/sda5        72G   67G  1.4G  99% /home
overflow        1.0M  1.0M     0 100% /tmp
nisarg@nisarg-ThinkPad-T61:~$ 
```
and here's my */etc/fstab* - 
```
nisarg@nisarg-ThinkPad-T61:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=02e7c4bc-7518-4115-a1ce-c6e27d1fe340 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=2f598827-cc61-4e9c-aed0-b86a9d923571 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
#UUID=66efe96d-e7a5-4e73-bd7b-2d99643ec328 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
nisarg@nisarg-ThinkPad-T61:~$ 
```
If it helps, before this error occured, I had used *extundelete* utility on an Ubuntu 10.10 live CD to recover some files on */dev/sda5*.

Any help will be appreciated.
Thanks!

***UPDATE: It seems the error has been resolved after I restarted my laptop (I am still confused as to what might have been the reason).***

---

### Post by deadflowr on 2014-05-17
Your root partition seems a little fat.
Maybe look into cleaning up some stuff.
Perhaps you have a few older kernels.
what does 
```
sudo apt-get autoremove
```
show?
Is there anything listed?

---

### Post by nisargshah on 2014-05-17
> **deadflowr said:**
> Your root partition seems a little fat.
Maybe look into cleaning up some stuff.

Yes its because I have kept some of my stuff here as my /home partition was full and I did not want to go into the headache of resizing.
> **deadflowr said:**
> 
Perhaps you have a few older kernels.
Yes I cleaned them using the *Ubuntu Tweak* tool.
> **deadflowr said:**
> 
what does 
```
sudo apt-get autoremove
```
show?
Is there anything listed?
```
0 upgraded, 0 newly installed, 0 to remove and 56 not upgraded.
```

---

