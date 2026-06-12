---
title: "Bad Superblock"
date: 2008-05-15
forum: General Help
---

### Post by dorian123 on 2008-05-15
Hello,

After upgrading to Ubuntu Hardy, I started having superblock corruption issues with one of my drives. On boot, fsck fails:

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda1
/dev/sda1:
The superblock could not be read or does not describe a correct ext2 filesystem. If the device is valid and it really contains an ext3 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock:
     e2fsck -b 8139 <device>

fsck died with exit status 8


After going into a root shell, e2fsck gives me the same error. 
So I tried a live CD. e2fsck on the live CD shows no problems with the drive. Using another superblock it found and supposedly fixed a bunch of errors. I rebooted, passed the check once or twice and failed again on another boot. I've done this more than once, fixing the superblock has become a daily activity.

So I tried formatting the drive, but still the same issue.

my fstab reads:

UUID=C250743C5074396D /home ext3 nodev,nosuid 0 2

Is this a problem with the hard drive? I can't understand why it boots fine once or twice and then the superblock gets corrupted again.
I Would appreciate any help... Thanks!!

---

### Post by rubicon on 2008-05-16
The prob seems to be with fstab, remove *nodev* option from the line (you may also remove *nosuid*, but I guess it is not necessary). For example, mine reads
```

UUID=b6e74233-c7f2-432f-ba86-5c388d07a0b6 /home           ext3    relatime        0       2

```

---

### Post by dorian123 on 2008-05-16
Thanks for you response rubicon. 

I modified my fstab to match my other drives:
UUID=.... /home ext3 defaults,error=remount-ro 0 2

Did not make a difference.

Also, since I reformatted the drive things have gotten worse. From a live cd I run 

efsck -f -y -b <superblocknumber> /dev/sda1 

and it finds a bunch of errors, and fixes them. If I run the same command again it finds the same errors. It's almost like it's not fixing anything. After a reboot I get the same problem. I haven't been able to fix the superblock since I formatted the drive. :confused:

---

### Post by dorian123 on 2008-05-16
I must add that running e2fsck on the primary superblock finds no errors! e2fsck on the live cd thinks my superblock is clean.
I only get errors with the backup superblocks.

---

### Post by kcponline on 2008-07-10
If your drive entries in fstab are /dev/hdaX, change them to /dev/sdaX and reboot.  This solved the problem for me!

---

