---
title: "mkfs strangeness after LVM dabbling"
date: 2004-11-01
forum: General Help
---

### Post by nicois on 2004-11-01
First, I'm very happy with what I've seen from Ubuntu. The only thing which would have been annoying was getting my atmel-compatible wlan card up - it would be great if it were distributed as a precompiled module.

Now, my big problem is that I can't use 40Gb of my disk. First the sequence of events:
- installed ubuntu (warty warthog) on a clean 60Gb disk. ~10Gb at the start with /root and /, LVM for 40Gb, leave 10Gb free for windows (just in case). Made 4 logical volumes, associated them with mountpoints, and everything was great
- rebooted into the devil: win2k. installed it in the empty space. lost my mbr and couldn't get the ubuntu install cd to just rewrite the MBR. didn't have much on ubuntu, so I thought i'd just re-install it over the top (reformatting the disks, and confirming the locations for lvm logical volumes

however, none of the logical volumes could be mounted! I can run mkfs.ext3 on each of them, though when I try mounting them, either from command-line or via fstab at bootup, I get:
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg0-home,
       or too many mounted file systems
The REALLY strange thing is when I deleted the LVs and the VG and formatted the partition (hda2) as ext3, I STILL couldn't mount it.

My only suspicion is that win2k has mangled the partition table so that it can't be mounted. I can't work out why mkfs works fine though.

Any ideas? Sorry if this turns out to not be ubuntu-related.

ps: kernel is 2.6.8.1-3-smp-686 if it makes any difference. all ubuntu updates are installed.

thanks for any advice.

---

### Post by cacofonix on 2004-11-01
I think the commands for making an ext3 partition are mke2fs -j /dev/blah. the other way looks way to complicated :D can you post a printout of this please:

1) sudo fdisk /dev/hda 
2) press p
3) copy the output

from what I can tell is windows is installed on the last sector of the drive and all before it are ignored (I may be wrong) 

cacofonix

---

### Post by nicois on 2004-11-01
Hi Cacofonix. Do you play the lute too?

Below is the output of fdisk. hda7 is / and hda5 is /boot. hda2 is the problem partition, which I set to 'linux' type when trying to get ext3 working. It said LVM earlier though. Oh, and hda6 is my swap.

I hope that helps. It's a strange one...

<...>

Oh sh*t! I re-ran mkfs and it's mounted!! So don't waste any more brain cells on this one. Perhaps I needed to reboot to resync my partition table? 
I'll try recreating the VG and LVs now, and see what happens.

Thanks for replying. You should be a shrink: help people just by listening to them.. :-)

Nick.

```

Disk /dev/hda: 61.4 GB, 61492838400 bytes
16 heads, 63 sectors/track, 119150 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       16567     8349736+   5  Extended
/dev/hda2           16568       74696    29297016   83  Linux
/dev/hda3   *       94073      119149    12638808    7  HPFS/NTFS
/dev/hda5               1          97       48825   83  Linux
/dev/hda6              98        1066      488344+  83  Linux
/dev/hda7   *        1067       16567     7812472+  83  Linux


```

---

### Post by cacofonix on 2004-11-01
I dont know what to do   ](*,) I might sugest posting it in the maillist forum you might be able to get your problem fixed in there

---

### Post by nicois on 2004-11-01
Well, I've solved my problem, but something looks a bit dodgy. Command-line mount works, but it's not mounting at bootup from fstab, nor does it use fstab for 'hints'.

I might raise it as a bug. Even if it's technically not, somehow, I imagine other people getting hurt by this one.

```

nick@sieben:~ $ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda7              7689760   2680536   4618604  37% /
tmpfs                   258008         0    258008   0% /dev/shm
/dev/hda5                45750     17036     26273  40% /boot
nick@sieben:~ $ sudo su
Password:
root@sieben:/home/nick # mount /usr/local/
mount: wrong fs type, bad option, bad superblock on /dev/mapper/vg0-Local,
       or too many mounted file systems
root@sieben:/home/nick # mount -t ext3 /dev/mapper/vg0-Local /usr/local/
root@sieben:/home/nick # mount -t ext3 /dev/mapper/vg0-Share /share/
root@sieben:/home/nick # df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda7              7689760   2679828   4619312  37% /
tmpfs                   258008         0    258008   0% /dev/shm
/dev/hda5                45750     17036     26273  40% /boot
/dev/mapper/vg0-Local
                      10321208    695304   9101616   8% /usr/local
/dev/mapper/vg0-Share
                      20642428    490660  19103192   3% /share


```

---

