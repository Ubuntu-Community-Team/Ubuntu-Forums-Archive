---
title: "[SOLVED] degraded RAID 1 boot drops me into BusyBox"
date: 2007-12-07
forum: General Help
---

### Post by jbulcher on 2007-12-07
Hi!

I just finished installing RAID 1 for the first time. It took me several days, and I got it set up and working properly with two disks; cat /proc/mdstat tells me the arrays are healthy. I also installed grub on both disks and can boot from either one of them, as long as they are both present to the system.

However, when I remove one of the disks to simulate a RAID failure, I can't get the system to boot. 
My raid is set up as follows:
/dev/sda1 + /dev/sdb1 = /dev/md0
/dev/sda2 + /dev/sdb2 = /dev/md1
/dev/sda5 + /dev/sdb5 = /dev/md3
/dev/sda6 + /dev/sdb6 = /dev/md4

Instead of booting, I get the following right before the boot installation pauses for a while:

```
md: md0 stopped.
md: bind<sda1>
md: md1 stopped.
md: md2 stopped.
md: md3 stopped.
md: md0 stopped.
md: unbind<sda1>
md: export_rdev(sda1)
md: bind<sda1>
md: md1 stopped.
md: bind<sda2>
md: md2 stopped.
md: bind<sda5>
md: md3 stopped.
md: bind<sda6>
```

After a few minutes, it will continue with:
```

Done.
stdin: error 0
Begin: running /scripts/local-premount ...
Done.
Usage: modprobe [-v] ..............
...
```

until it drops me into Busybox.

How can I get the box to boot with one disk, so I can test rebuilding the RAID?

Thanks in advance for your help.

---

### Post by jaakan on 2007-12-07
does the same thing happen with the drive you pulled out in and the drive thats in out?

---

### Post by jbulcher on 2007-12-10
> **jaakan said:**
> does the same thing happen with the drive you pulled out in and the drive thats in out?

Yes, it does

---

### Post by psusi on 2007-12-10
Known issue... manually run mdadm to start the array in degraded mode, then exit from the busybox shell to continue booting.

---

### Post by jbulcher on 2007-12-10
Awesome. Thanks for your help!

Do you know where I can get more information on this topic?

---

### Post by jbulcher on 2007-12-10
Actually, let me as a more important question - how do I mark the array as degraded? I though I could just mark the disk as failed and then remove it. However, the command
```
mdadm --manage /dev/md0 --fail /dev/sdb1
``` tells me: ```
mdadm: cannot get array info for /dev/md0
```Am I on the right track to mark the array as degraded? do I just need to perform a different command before I can execute --fail?

---

### Post by psusi on 2007-12-10
I think you just want to start it with --run.  Once started with a disk missing, it will automatically be marked as degraded.

---

### Post by fjgaude on 2007-12-10
I don't think you need the --manage mode to declare a drive failed:

```
sudo mdadm /dev/md0 -f /dev/sdb1
```

Try that and see what happens... I tell you we have to carefully read the man page to understand just what command to use and when.

---

### Post by jbulcher on 2007-12-10
psusi:
ok, so now the array is running, as I can see with cat /proc/mdstat. Now how do I boot the computer? If I reboot, I'm back to square 1without a working /dev/md0, and if I try to exit BusyBox, it tells me: ```
Target filesystem doesn't have /sbin/init
``` and drops me back into busybox. Do I just need to manually mount everything linux would normally automatically mount? mount -a doesn't work, as /etc/fstab isn't available

fjgaude:
it no longer seems necessary to manually mark devices as failed and remove them, since the run command appears to get the degraded array running. I think I understand now that the command can only be used if the devices are currently available to the system, since if I try to fail a device BusyBox tells me that the device doesn't exist. Which it doesn't - so that's fine.

---

### Post by jbulcher on 2007-12-10
Ok, I've been doing troubleshooting on and off all day, but I think I'm coming closer to the source of the problem. I used "mdadm --run" on /dev/md0, and then mounted the filesystem. At first it didn't seem to do anything, because I was in BusyBox, and I mounted it to / - and something was already mounted there (?) - anyway, I rebooted, and this time [drum roll] the computer booted!

point 1 for the good guys.

However, none of the other file systems mounted, which can only mean one thing (I think); mounting the file system affects how mdadm treats the array on boot. I tried it again for one of the other partitions, and that one also mounted upon reboot.

point 2 for the good guys

Then I though, well this isn't so bad, I can just mount everything and reboot to get the computer working again, when it hit me: you can't mount the swap. And that part of the array (/dev/md3) isn't working either.

3 points for the bad guys. (dang)

So I think this is what I need to understand in order to fix this... problem: what is happening when I mount a file system that makes mdadm use it upon reboot, and how can I do that to /dev/md3 (the swap file system)

I'm so close! any help is appreciated!

---

### Post by jbulcher on 2007-12-10
well, I've stumbled across this [bug]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/125471") which suggests that using mdadm --run aught to work; unfortunately I seem to be the odd case that it doesn't work for. Anyone have any suggestions?

---

### Post by fjgaude on 2007-12-10
Thanks for the update. I long ago decided, because of advice recieved, that to never use raid arrays to boot a system. I use raid only for data and a single separate drive to boot from. It has worked well.

I know of no big systems booting from raid. There may be some but I can't say where.

I can see that Linux kernel and mdadm has a ways to go before perfection is achieved. <smile>

---

### Post by jbulcher on 2007-12-11
thanks for the reply fjgaude.
The funny thing is I can get the system to boot, if I get the root partition running indegraded mode AND mount it somewhere. It's the mounting that gets mdadm to play nice. But I can't do that with the swap partition. What goes on during the mount that doesn't happen when I use "mdadm --assemble --scan (--run)"? Is data written to the drive for the 1st time perhaps? Is there another way to write data to the drive (the superblocks, I think) without mounting the file systems?

I begin to see why you haven't come across any big systems booting from RAID :)

---

### Post by jbulcher on 2007-12-11
I figured it out! Here's the solution:

After you wait for the machine to boot into BusyBox (takes a few minutes) run these commands:

```
mdadm --assemble --scan
mdadm --stop
reboot
```

the option --scan allows the --assemble mode to read the composition of the raid devices from the disks themselves (I think. But where else could it get the info from?) - anyway, if you don't use --scan you either have to specify the composition of the md devices, or the UUID of the partition you want to start. This may be desirable, because --scan isn't picky about which arrays it starts.

--stop does the real work so that the degraded mode persists upon reboot. That way mdadm knows that it should boot the disks.

reboot is self-explanitory.

Time to CELEBRATE!
P.S. Thanks for your help!!

---

### Post by dbodden on 2008-03-09
I was able to get the boot partition to mount as degraded raid 1.

I noticed that previous posts in this thread mention using mdadm to start the raid-1 arrays degraded, but not how to mount the filesystems.

From busybox:

mkdir /boot
mount -t <fstype> /dev/md0 /boot

I did this for my /root and /home partitions as well. Since /root was already created in the busybox shell, I did not have to explicitly create it with mkdir, but I did with my /home data partition.

Did this work for you?

---

### Post by jbulcher on 2008-03-13
I think we only had two partitions on the raid drive; '/' and the swap partition - consequently I never had to create a directory to mount the partitions.

Why would you want to do that though, when you can just mark the partitions as degraded? As soon as you make changes to the file system the raid array won't be in sync anymore anyway.

---

### Post by dbodden on 2008-03-16
The only way I could get my system to boot required me to explicitly mount the filesystems after marking the arrays degraded from busybox.  It may not be the "right" way, but it was all I could get working.

---

