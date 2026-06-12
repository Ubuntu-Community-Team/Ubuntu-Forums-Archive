---
title: "Upgraded to 7.10 lost Raid5 Array (please tell me I can rebuild it!)"
date: 2007-11-07
forum: General Help
---

### Post by hevnsnt on 2007-11-07
Well I finally made the upgrade to 7.10, and everything is working great...... EXCEPT my Raid drive is missing!  I created this raid5 array awhile ago, using one of the walk-thoughs online, and I have a lot of documents on there that I need to get back, so Please tell me that it isnt any big deal getting this array back! (and please help walk me through it)

My system is as follows:
/dev/sda1 150gb mounted as /

/dev/sdb 500gb flagged as raid
/dev/sdc 500gb flagged as raid
/dev/sdd 500gb flagged as raid

When I run a mount /dev/md0 I get the following:
> 
root@linuxbox:/etc# mount /dev/md0
mount: you must specify the filesystem type

but when I check my /etc/fstab I clearly see the line 
/dev/md0  /var/nasstorage  auto  defaults  0  3

so then I run:
mdadm --assemble --scan --verbose 
and I get the following output
> root@linuxbox:/etc# mdadm --assemble --scan --verbose
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdd1 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdd
mdadm: /dev/sdd has wrong uuid.
mdadm: /dev/sdc1 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdc
mdadm: /dev/sdc has wrong uuid.
mdadm: /dev/sdb1 has wrong uuid.
mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: no devices found for /dev/md0
root@linuxbox:/etc# mdadm -R /dev/md0
mdadm: failed to run array /dev/md0: Invalid argument

I do have a /etc/mdadm/mdadm.conf file, but I am not sure what exactly to make of it, it contains:

> DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=7e43c9ac:2b1fbfbe:f7137588:1298fb94
MAILADDR root

Can anyone help me re-assemble this array and mount it back to /var/nasstorage?

Thanks!

---

### Post by fjgaude on 2007-11-07
I have a raid5 array built under 7.04 and it is  working fine with 7.10. No need to rebuild.

I think the first thing to do is to see what the UUID is of the array under 7.10:

```
sudo vol_id /dev/md0
```

Then use that in your mount in fstab. I would rename the mdadm.conf file to mdadm.conf.bak and see if things are back to normal, after rebooting.

Let us know how things go.

---

### Post by hevnsnt on 2007-11-07
Hey I really do appreciate the help, here is the result when I issue that command.

> sudo vol_id /dev/md0
/dev/md0: unknown volume type

---

### Post by fjgaude on 2007-11-07
Oh boy, what does sudo fdisk -l show? and mount show?

Something is very strange here for sure. Somehow we will get to the bottom of it all, eh?

---

### Post by hevnsnt on 2007-11-07
> root@linuxbox:~# fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000772de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19745   158601681   83  Linux
/dev/sda2           19746       19929     1477980    5  Extended
/dev/sda5           19746       19929     1477948+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384015+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384015+  83  Linux
root@linuxbox:~# 

> root@linuxbox:~# mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

Once again, I really do appreciate the help... Hopefully the above means more to you than it does to me in relation to the software raid!

---

### Post by fjgaude on 2007-11-07
Wow, two of the drives in the raid array use GPT (not MBR which is more usual) but one of them doesn't, the sdc.

I'll have to get back with you. Can you tell me how you created the array, and what has been done to it since that creation?

---

### Post by diggity on 2007-11-10
I have had the same problem. I found that if I boot with the 2.6.20-16-generic kernel, the raid works fine. If I find out anymore information, I'll be sure to post it.
Try running an older kernel and see if that works.

---

### Post by fjgaude on 2007-11-10
Very strange, I had no trouble going from Feisty to Gutsy with my raid5 array, none. The only thing I did was start with one of the early releases, alpha 4 I think, and kept updating as the time went on, right to the release of 7.10. Then I did nothing more. The array always came right up in my dual boot system, 32- and 64-bit 7.10s.

I originally made the array in early Feisty release, likely about last June. Runs great, fast as my PCI bus will permit. Ready for an PCI-E controller. <smile>

---

### Post by hevnsnt on 2007-11-10
> **diggity said:**
> I have had the same problem. I found that if I boot with the 2.6.20-16-generic kernel, the raid works fine. If I find out anymore information, I'll be sure to post it.
Try running an older kernel and see if that works.

Thank you both for your help -- I booted to 2.6.20-16 and sure enough my array is back! YEAH -- currently backing everything up.. =)

Now -- anyone have any idea how to make it work with other kernel! :)

---

### Post by hevnsnt on 2008-01-07
I would like to bring this back up.. My raid continues to work as long as I boot to kernel 2.6.20-16, if for some reason my system restarts and I dont select that kernel, it boots to 2.6.22-14 and my Raid is missing.

Can anyone solve this mystery?

---

### Post by fjgaude on 2008-01-07
Have you tried using the mdadm -f command to assemble the array in the 2.6.22-14 kernel?

Do you have a valid mdadm.conf file in /etc/mdadm?

Since I've never seen the issue you face I can't say what to do other than this:

```
sudo mdadm --assemble --scan --force
```

You might wish to read, study this version of the man pages:

[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

Let us know how you do.

---

### Post by hevnsnt on 2008-01-07
> **fjgaude said:**
> Have you tried using the mdadm -f command to assemble the array in the 2.6.22-14 kernel?

Do you have a valid mdadm.conf file in /etc/mdadm?

Since I've never seen the issue you face I can't say what to do other than this:

```
sudo mdadm --assemble --scan --force
```

You might wish to read, study this version of the man pages:

[http://man-wiki.net/index.php/8:mdadm](http://man-wiki.net/index.php/8:mdadm)

Let us know how you do.

thanks for the help, but as you can see from my first post I tried this first.  :(

---

### Post by fjgaude on 2008-01-07
You say you did try the --force option?

---

### Post by hevnsnt on 2008-01-09
Here was my result

```
hevnsnt@linuxbox:~$ sudo mdadm --assemble --scan --force
[sudo] password for hevnsnt:
mdadm: No arrays found in config file
hevnsnt@linuxbox:~$ 
```

---

### Post by tad1073 on 2008-01-09
bump

---

### Post by tad1073 on 2008-01-09
Do you think you can tell me how to get 7.10 installed on a raid? Here are my specs:
Compaq Proliant ML330
Pentium III 733mhz 256k cache
256mb ram
Compaq Smart Array 431 Controller set to RAID0 w/25.9gb=3/9.1gb hd's
System Embedded IDE Controller
SCSI Controller

---

### Post by fjgaude on 2008-01-09
> **hevnsnt said:**
> Here was my result

```
hevnsnt@linuxbox:~$ sudo mdadm --assemble --scan --force
[sudo] password for hevnsnt:
mdadm: No arrays found in config file
hevnsnt@linuxbox:~$ 
```

Wow, this is the problem... now how to get one.

The man pages show how. Did you try it?

Something like this might get you a conf file. Place it in /etc/mdadm directory:

```
 echo 'DEVICE /dev/hd[a-z] /dev/sd*[a-z]' > mdadm.conf
 mdadm  --examine  --scan --config=mdadm.conf >> mdadm.conf
```

I guess I've never seen a situation like you have... that conf file is created as soon as you create an array with mdadm, AFAIK.

---

### Post by fjgaude on 2008-01-09
> **tad1073 said:**
> Do you think you can tell me how to get 7.10 installed on a raid? Here are my specs:
Compaq Proliant ML330
Pentium III 733mhz 256k cache
256mb ram
Compaq Smart Array 431 Controller set to RAID0 w/25.9gb=3/9.1gb hd's
System Embedded IDE Controller
SCSI Controller

Your requested is beyond by ability. I don't think you can do it, but others may have different ideas.

---

### Post by hevnsnt on 2008-01-10
I do appreciate your help.. 

```

hevnsnt@linuxbox:~$ echo 'DEVICE /dev/hd[a-z] /dev/sd*[a-z]' > mdadm.conf
hevnsnt@linuxbox:~$ mdadm  --examine  --scan --config=mdadm.conf >> mdadm.conf
root@linuxbox:/etc/mdadm# cp /home/hevnsnt/mdadm.conf .
root@linuxbox:/etc/mdadm# mdadm --assemble --scan --force
mdadm: No arrays found in config file

```

The mdadm  --examine  --scan --config=mdadm.conf >> mdadm.conf returns nothing..  I did find a mdadm.conf file that I had backed up before upgrading, so I reinstated it and tried the force.. Got a different result, still did not work.

File generated using your commands:
```

root@linuxbox:/etc/mdadm# cat mdadm.conf
DEVICE /dev/hd[a-z] /dev/sd*[a-z]
root@linuxbox:/etc/mdadm# 

```

Previous file:
```

root@linuxbox:/etc/mdadm# cat mdadm.conf.bak 
DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=7e43c9ac:2b1fbfbe:f7137588:1298fb94
MAILADDR root
root@linuxbox:/etc/mdadm# 

```

When I attempt to run the assemble command using the previous mdadm.conf I get this result:
mdadm: error opening /dev/md0: No such device or address

so....

root@linuxbox:/dev# ls md0 
md0
root@linuxbox:/dev#

---

### Post by fjgaude on 2008-01-10
All this is so strange... when and how did you get that mdadm.conf backup file? Do you remember when the array actually worked correctly?

I'm at a loss... what to do next? Use backup superblocks on each disk?

Okay, the title of this thread reminds me of where you started: it was the upgrade that caused the issue?

---

### Post by hevnsnt on 2008-01-10
> **fjgaude said:**
> All this is so strange... when and how did you get that mdadm.conf backup file? Do you remember when the array actually worked correctly?

I'm at a loss... what to do next? Use backup superblocks on each disk?

Okay, the title of this thread reminds me of where you started: it was the upgrade that caused the issue?

Tell me about it! :confused::confused:

Ok some history: I built the Raid using 6.06 was working great and decided to upgrade to 7.10.  When I booted into 7.10 I found that my array was missing!!  So I read a bunch of wiki's etc and decided that it was best to backup what I had already (where the mdadm.conf.bak came from) and create a new mdadm.conf file.  Going through the same steps that we just did I found that mdadm couldnt scan my array.  That is when I started this post.

We tried a bunch of the same stuff again, and it wasnt working until the post about booting to the previous kernel came into play.  So I tried that and to my amazement it worked (even with mdadm.conf renamed to .bak) so I kind of just lived with it.

But I would like to get it fixed!

---

### Post by fjgaude on 2008-01-10
Okay, and thanks for explaining in so direct terms for me. 6.06, gosh!

The issue, and I guess I should have known this at first, is the kernel used in 6.06 is so different than in 7.10 in the way md is handled. If memory serves, mdadm is not even used in 6.06. Correct me if I'm wrong.

I tell you, one way is to recreate array in 7.10... that's the last resort. <sigh>

The issue is how the UUIDs and drive names are figured out. You see 6.06 and 7.10 do it AFAIK in different ways. So in 7.10 it is seeing an array UUID that is can't handle.

What we need to do is figure out how to get a new UUID for the array while in 7.10. The LiveCD for 7.10 is the only way I can think of right now, and I've never done such before. In the LiveCD we have to assemble the array and get the UUID developed.

Maybe someone here will see this and help. Help, guys! If not, start a new thread with your last post and see what happens. We will get to the bottom, with patience! <smile>

---

### Post by hevnsnt on 2008-01-10
honestly I think I am going to just change my lilo.conf to point to the 2.6.20-16 kernel and live with it.. This box is pretty much only used as a NAS anyway..

:)

---

### Post by fjgaude on 2008-01-10
As you wish... Linux has been going through many changes to be able to handle adding and removing devices, drives and still have the OS function. It is still not perfect as far as I can see with the UUID and its translations. I guess some of it could be that going from one kernel update to another we are left short of perfection. Likely 2.6.22 has it right, but I'm not sure. Time will tell.

---

### Post by hevnsnt on 2008-01-11
haha I just got home to do this and realized Ubuntu uses grub by default.. 

:)

---

### Post by fjgaude on 2008-01-11
What does this mean for the issue at hand? Please, I don't get it.

---

