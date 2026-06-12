---
title: "Clone won't boot"
date: 2014-07-28
forum: General Help
---

### Post by ken18 on 2014-07-28
I have 12.04LTS installed on a solid state drive in a Lenovo T61 laptop.  I've tried cloning the drive to an HDD (attached via USB) using two methods: clonezilla and Apricorn SATAWire/EZGIGIII.  In both cases the cloning occurs without any error at all, but I can't get the clone to boot via USB (I know USB boot works because I have a separate HDD with Linux that boots ok from USB).  Also, when I boot Ubuntu and then attach the clone via USB, it isn't mounted.  I can see the clone in disk utility as /dev/sdb, but it's not mounted and I get a mount error if I try to mount it.  Other USB devices work just fine, including the previously mentioned Linux drive.  

I'm baffled.  What's going on?   Any advice would be greatly appreciated.

Ken

P.S. The original capacity of the SSD is slightly higher than the HDD, so I clipped the SSD using hdparm before installing Ubuntu.  Now the SSD has the same # LBA's as the HDD.

---

### Post by yancek on 2014-07-28
Using clonezilla, did you clone the entire drive or just the partition?  If it was the partition I would not expect it to work without modifying the boot menu.

If you have ubuntu on a separate drive/partition, have you checked under the /media directory to see if it is there?

You forgot to post the mount command you used when you got the error,  there's no way anyone will be able to tell you if something is amiss there.

---

### Post by ken18 on 2014-07-28
Thanks for your reply.  I cloned the entire drive, which consists of two partiions, a 6GB swap partition and a bootable EXT4.  I can see both partitions using the disk utility.  Re mount command, I just use the mount button in the disk utility.  The error message says there is already a drive mounted at /.  I'll try a command line version of mount tonight.  What I don't understand is why another Linux drive I have will (1) boot ok from USB and (2) mounts just fine when I attach it after booting to the original drive, whereas the clone will do neither.  Either I made some mistake installing Linux in the first place or something about the cloning process is wrong.

---

### Post by steeldriver on 2014-07-28
The mount error is probably because the cloned partitions (or, more specifically, the filesystems on them) have UUIDs that duplicate the originals still on the same box - it would likely mount OK on an entirely separate system. You should be able to use tune2fs to set truly unique UUIDs for any ext filesystems on the cloned devices.

---

### Post by Bucky Ball on 2014-07-28
You could unplug all other drives bar that one, boot from a Boot Repair disk/USB and try fix the boot that way. 

Still a bit confused; you are changing the BIOS and booting from that drive or you are disconnecting the other drives? If you are booted into the hard drive install and trying to mount the drives on the clone:
```

sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
```

Should be there, all going to plan ...

* PS: When cloning the whole disk, not sure if that includes the MBR or just the partitions. You might want to check on that. If the latter then it won't boot without installing Grub. Boot Repair can do that or you can do it manually.

---

### Post by ken18 on 2014-07-29
Using tune2fs to change the filesystem UUID of the clone worked for being able to mount it.  OK, problem #1 solved, thanks for the tips.  Re booting, I'll re-ask the question more simply:

How does one verify that the cloning operation (including MBR/bootloader) was a complete success?  In other words, I want to verify that the clone will successfully boot (in case I have to replace the original at some point with the clone). I read somewhere something about having to edit grub/stab files, but I'm hoping there is a much more simple way (other than physically removing the original and replacing it with the clone).

Ken

---

### Post by Bucky Ball on 2014-07-29
As I say, Boot Repair may be able to do this for you, but editing the UUIDs in /etc/fstab is a cinch. 

Open one terminal and:

```
sudo blkid
```

Open another terminal and:

```
sudo nano /etc/fstab
```

Check the UUIDs from the output of 'sudo blkid' with the ones in the entries in your fstab. If they are wrong in fstab, change 'em. Ctl+x, 'y', to save and exit, then reboot.

I was figuring the fstab would probably be a mess when you plop on the clone. I used Boot Repair when I did this myself (cloned a Win XP and Ubuntu partition, put them back on a new SSD, ran Boot Repair, done).

---

### Post by ken18 on 2014-07-30
I found a way to boot the clone without modifying the fstab file:

(1) boot another Linux drive via USB (Ubuntu live CD should work also)
(2) modify filesystem UUID of the original drive
(3) shut down
(4) clone will now boot via USB
(5) repeat (1) and (2) to change UUID back to the original value

After (5), it took two attempts for the original drive to boot.

Ken

---

