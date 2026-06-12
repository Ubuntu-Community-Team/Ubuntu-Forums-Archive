---
title: "Raid 1 in gutsy"
date: 2007-10-31
forum: General Help
---

### Post by Woody1987 on 2007-10-31
Hi i am trying to create a raid 1 setup on my gusty 64 box. I have already installed mdadm and have attempted to create a raid but to no avail. I have tried many different howtos in these forums and everywhere else on the internet.

My setup is:

2 x 500gig sata
1 x 250gig ide

i currently have vista (:lolflag:) installed on the 250gig hdd and i want to keep it there and not mess with it at all. In fact any help you give just completely ignore it. Anyway, i want to create a raid 1 using the other two hdd's to which i will install gutsy 64. I am using the livecd with mdadm.

i need help knowing how to partition my drives, how to create the actual raid after this and also when i install gutsy, what to? and will my raid automatically work when i boot into it?

Any help is appreciated. Thx.

---

### Post by fjgaude on 2007-10-31
You might want to take a look at these:

[HTML]http://ubuntuforums.org/showthread.php?t=464758[/HTML]

[HTML]http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Configuring_Software_RAID[/HTML]

Lots of things to learn to get to be where you wish to go.

---

### Post by Woody1987 on 2007-10-31
ok, i followed the guides given and i have partitioned and created my raid 1.

When i run cat /proc/mdstat i get:

```

root@ubuntu:~# cat /proc/mdstat 
Personalities : [raid1] 
md0 : active raid1 sdb1[1] sda1[0]
      478142464 blocks [2/2] [UU]
      [>....................]  resync =  4.5% (21762176/478142464) finish=95.9min speed=79260K/sec

```

i presume i need to wait for this to get to 100% before i install anything. 

The only other problem i can forsee is that when i install gutsy where do i install it to? do i install it to one of the 500gig disks, and assume that due to the raid, that the data will be put onto both? or will there be an option to install to my newly created raid, /dev/md0?

---

### Post by fjgaude on 2007-10-31
You know, I don't know because I've never done such.

I would start with the LiveCD and see if it saw the md0 array. If it does you are home free to install it there. But if it doesn't, then you may try to install on only one of the disk. and then mdadm will likely auto copy one drive to the other, completing the raid1 array.

If you do a Google search you might be able to find someone who has done exactly what you need.

Okay, this just in:

[HTML]http://nixcraft.com/getting-started-tutorials/432-setting-up-raid-1-mirroring-running-remote-linux-system.html[/HTML]

Good luck and let us know how you make out.

---

