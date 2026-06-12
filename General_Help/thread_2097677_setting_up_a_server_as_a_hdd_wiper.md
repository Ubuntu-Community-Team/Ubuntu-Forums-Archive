---
title: "setting up a server as a hdd wiper"
date: 2012-12-24
forum: General Help
---

### Post by dcody on 2012-12-24
Hello - I am trying to use an intel based 2u sata server as a hdd wiper/formater. I have about 150 hdd's that I need to wipe and prep for resale. I have installed ubuntu 12.10 on a 160 sata drive in bay one (has a total of 8 bays). 

It would be ideal if I could load the bays with drives and set it up to wipe one after the other or all at once. 

Currently I don't know how to get ubuntu to recognize the drives I want to wipe. 

I am a 10 year ubuntu user and a novice under the hood. I have very little server experience. 

I have been searching but I am not finding anything that matches my situation. 

Anyone have an idea how this could work out. Thanks a ton.

---

### Post by Wim Sturkenboom on 2012-12-24
Check with _sudo fdisk -l_ (that is, lowercase L at the end) which disks are there.

```

wim@aa0:~$ **[COLOR="Red"]sudo fdisk -l[/COLOR]**

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003255d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         918     7367680   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             918         981      509953    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             918         981      509952   82  Linux swap / Solaris

Disk /dev/sdb: 4127 MB, 4127195136 bytes
127 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 7874 * 512 = 4031488 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000451df

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1023     4027520    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 126, 62) logical=(1022, 126, 62)
wim@aa0:~$ 

```
In the above, there are 2 disks, /dev/sda (my system disk) and /dev/sdb (an additional disk). You will get a few more (sdc, sdd etc, one for each disk inyour system)

Make sure the partitions on the non-system disks are not mounted.
```

wim@aa0:~$ **[COLOR="Red"]mount[/COLOR]**
/dev/sda1 on / type ext4 (rw,noatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/sdb1 on /media/PENDRIVE type vfat (rw,nosuid,nodev,uhelper=hal,uid=1000,shortname=winnt)
wim@aa0:~$ 

```
In this case, partition 1 (/dev/sdb1) of disk2 (/dev/sdb) is mounted. You need to unmount all partitions of the non-system disks if they are mounted.
```

wim@aa0:~$ **[COLOR="Red"]sudo umount /dev/sdb1[/COLOR]** 
wim@aa0:~$ 

```

Next you can wipe the disk by overwriting it with zeros using the _dd_ command
```

**[COLOR="Red"]sudo dd if=/dev/zero of=/dev/sdb[/COLOR]**

```
Repeat for sdc, sdd etc. MAke sure that you don't overwrite you system disk which is probably /dev/sda.

You can force the commands to the background by adding an ampersand at the end
```

**[COLOR="Red"]sudo dd if=/dev/zero of=/dev/sdb &[/COLOR]**

```
Personally I would rather open multiple consoles / terminals and run each 'dd' in its own terminal so you can more easily check when they are done.

Note that the process can take long. For a normal wipe this should be enough; normal users will not be able to get data back that is wiped that way. I'm not that paranoid that I will overwrite with /dev/random and do multiple wipes so I will use /dev/zero.

One link that I found:
[http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux](http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux)

Note:
commands in red bold

---

### Post by Grenage on 2012-12-24
As an addition to the excellent advice already received, assuming that you're using a server with true RAID, your drives may well show up more like:

```
/dev/cciss/c0d0
```

rather than:

```
/dev/sda
```

Merely because of the controller.

It may also be worth stipulating a large block size when using dd (4096 or so), although I'm not sure if that will have a great impact on a zero session.

---

### Post by Cheesemill on 2012-12-24
Just to add to Win Sturkenboom's post you can increase the speed that dd runs at by adding the bs (block size) argument:
```
sudo bs=4MB if=/dev/zero of=/dev/sdb
```

---

### Post by Wim Sturkenboom on 2012-12-24
Note:
the fact that you're using server hardware can make a difference for what you see in the fdisk output. If not sure, post the output of the first command.

//Edit
just see that Grenage already covered that.

---

### Post by Wim Sturkenboom on 2012-12-24
> **Cheesemill said:**
> Just to add to Win Sturkenboom's post you can increase the speed that dd runs at by adding the bs (block size) argument:
```
sudo bs=4MB if=/dev/zero of=/dev/sdb
```That is shown in the link that I provided. I however have a question about that (without trying to hijack the thread): **[COLOR="Blue"]what is the optimal size for the bs parameter or how to determine the optimal size?[/COLOR]**

---

### Post by Grenage on 2012-12-24
> **Wim Sturkenboom said:**
> what is the optimal size for the bs parameter or how to determine the optimal size?

It's completely system-dependant, not least of course - the drives themselves.  With modern drives, I imagine one could happily use 8-16M chunks, given the abundance of cache.

---

### Post by Wim Sturkenboom on 2012-12-24
> **Grenage said:**
> **It's completely system-dependant**, not least of course - the drives themselves.  With modern drives, I imagine one could happily use 8-16M chunks, given the abundance of cache.
I understand that ;) I was thinking about a more scientific answer :lolflag:

Block size? HD buffer size? What else?

Reason for asking is that I (sorry, my system) just has spend roughly 30 hours running creating an image of a 125GB partition (bs was 1M) to (OK, I admit) an USB2 external HD.

---

### Post by Grenage on 2012-12-24
> **Wim Sturkenboom said:**
> I understand that ;) I was thinking about a more scientific answer :lolflag:

Block size? HD buffer size? What else?

Reason for asking is that I (sorry, my system) just has spend roughly 30 hours running creating an image of a 125GB partition (bs was 1M) to (OK, I admit) an USB2 external HD.

I'd probably push the BS to the cache size, although with USB, I don't think it's going to make much difference. ;)

Alas, I fear we have derailed this thread some!

---

### Post by dcody on 2012-12-24
Thanks for the help - I will be back a my workstation in about 2 hours and run fdisk and post output - last time I ran it it only showed one disk - I will run it again. Thanks.

---

### Post by Wim Sturkenboom on 2012-12-24
You might have to configure your hardware. I'm only a little bit familiar with HP servers and I need to sit behind one to find the exact terms, but I guess you need to configure the raid arrays.
Make and model of your server might help people to help you.

---

### Post by dcody on 2012-12-24
Hi - just got back to my space - here is the fdisk output. I am using a custom built server running ubunut 11.10 i386. 


Disk /dev/sda: 160.0 GB, 159988580352 bytes
255 heads, 63 sectors/track, 19450 cylinders, total 312477696 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00041e81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   304091135   152044544   83  Linux
/dev/sda2       304093182   312475647     4191233    5  Extended
/dev/sda5       304093184   312475647     4191232   82  Linux swap / Solaris


I have 3 disks total installed at the moment - it seems only one is being recognized. Thanks

---

### Post by dcody on 2012-12-24
whenever I put in another disk it is not regonized by fdisk - I am sure I am missing something simple. 

Once the system is running - how do I get the system to see the hdd I want to wipe?

---

### Post by dcody on 2012-12-24
> **Wim Sturkenboom said:**
> You might have to configure your hardware. I'm only a little bit familiar with HP servers and I need to sit behind one to find the exact terms, but I guess you need to configure the raid arrays.
Make and model of your server might help people to help you.

the fdisk output is posted - how do I get ubu to recognize the other disks? Thanks

---

### Post by dcody on 2012-12-24
Hello - I am still stuck on this if anyone can help me out that would be great. Thanks

---

### Post by dcstar on 2012-12-24
> **dcody said:**
> whenever I put in another disk it is not regonized by fdisk - I am sure I am missing something simple. 

Once the system is running - how do I get the system to see the hdd I want to wipe?

Hot-plugged SATA drives will only be recognised in AHCI mode. If your BIOS does not support AHCI then you need to reboot after every drive change.

---

### Post by Wim Sturkenboom on 2012-12-25
> **dcody said:**
> Hello - I am still stuck on this if anyone can help me out that would be great. Thanks
Please stop pushing your thread. Some people need to sleep or are having a Christmas dinner.

In post #11 I asked for make and model of the server so knowledgeable people (probably not me) can help further. Still no reply on that one.

---

### Post by Cheesemill on 2012-12-25
As you are using server grade hardware then when you plug in a new drive it is almost definitely being connected to your hardware RAID controller via the drive backplane instead of being connected directly to the motherboard.

To get your new drives to show up on the host OS as individual drives rather then part of a RAID array you need to make changes in your RAID cards BIOS, this is reached by pressing a key as the system boots up. This key is different from card to card so either keep an eye out for the message that appears on screen or take a look at the manual for your hardware.

Once in the RAID cards BIOS you need to set it to present individual drives to the OS, this is usually called JBOD mode (**J**ust a **B**unch **O**f **D**isks). Until you get back to us with the specs of your hardware then this is the best help we can give you.

---

