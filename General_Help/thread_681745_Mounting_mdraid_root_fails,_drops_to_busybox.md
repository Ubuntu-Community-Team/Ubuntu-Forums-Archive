---
title: "Mounting mdraid root fails, drops to busybox"
date: 2008-01-29
forum: General Help
---

### Post by shiver on 2008-01-29
I have found several bug reports and threads about mdadm issues as well as a suggestion for software raid support overhaul in Ubuntu which I wholeheartedly agree with, but my problem seems to be a little different than anything I found.

I run the x86_64 version of Feisty with all my partitions except the backups as mdraid 0. When booting, there is some race condition issue that sometimes causes the sequence to stop with the error message:

mounting /dev/md0 on /root failed: Device or resource busy


where md0 is my root partition. Then I'm left with a Busybox shell and I have to mount /dev/md0 to /root myself and hit ctrl-d to proceed.
This happens about every third time I boot. Is there any clean way to fix it? If it's fixed in Gutsy or Hardy, I'm satisfied too, although I'm not going to upgrade anytime soon. I could live with it.

---

### Post by fjgaude on 2008-01-29
What does your /etc/fstab look like? Maybe by moving some of the lines forward or backward may correct the race issue.

---

### Post by shiver on 2008-01-30
Thanks for replying.

My fstab is a bit of a mess, the ones set by the installation are listed by UUID and those I have added later are by device name:

```

# /dev/md0
UUID=a34fe813-324d-465a-806e-4c1a79b089d5 /               ext3    noatime,errors=remount-ro 0       1

# /dev/sda2
UUID=e7ba988d-c14a-4afb-9c37-7c77c3badbbf /boot           ext2    noatime         0       2

/dev/md1                                  /home           jfs    noatime         0       2

# /dev/sdb1
#UUID=f571994c-5980-4329-b229-01e1ef301f26 /media/backup   xfs     noatime         0       2

/dev/md2                                  /data           jfs     noatime         0       2
/dev/md3                                 /app             jfs     noatime         0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0



```

I came up with the idea that the mounting could be blocked because mdadm is still busy assembling the array. Here's my mdadm.conf:

```

ARRAY /dev/md0 level=raid0 num-devices=2 UUID=fdcc8e8c:7ccf6a59:fd57d9f0:a5339b6a
ARRAY /dev/md1 level=raid0 num-devices=2 devices=/dev/sda5,/dev/sdc3
#ARRAY /dev/md1 level=raid0 num-devices=2 UUID=a31c1942:1645bf07:c3c91ccb:50087f22
ARRAY /dev/md2 level=raid0 num-devices=2 UUID=cf2a5828:c73a0508:68e96de4:e0ffb050
ARRAY /dev/md3 level=raid0 num-devices=2 UUID=a0aba50d:4076ae71:c0b05b25:c8dc73d3

```

I once lost the md1 partition because of some raid metadata corruption and built it again from backups, that's why the entries have been fiddled with, too. :)

How should I change the config files? Isn't the root partition always mounted first anyway? Even if I manage to change the assembly/mount order, couldn't mounting some other partition get blocked instead? Seems like the only way to do it properly would be to have the mount operation wait or retry until it succeeds.

---

### Post by fjgaude on 2008-01-30
You might try moving your /dev/sda2 to the first of the fstab list and see what happens.

I guess you know that many of us don't recomend booting from raid, except from a raid card that has a driver for Ubuntu.

The module that mdadm uses is "md" and it is in the kernel.

More to learn, day-by-day.

---

### Post by shiver on 2008-01-30
I'll try that and report back when/if it works or not. It's not a big deal, really. I usually would suspend to ram anyway and would have to (re)boot very rarely. I haven't been able to do that because my PSU became faulty and couldn't keep the system powered when going to STR. I'll have that fixed soon.

And I knew raid (esp. 0) is not very good for a root partition. I just wanted to try it out once. :)

---

### Post by shiver on 2008-02-07
It didn't work, the boot hung again. :\

---

### Post by fjgaude on 2008-02-07
I can't think of anything to tell you to try. Maybe someone here has some ideas.

---

### Post by astrotech226 on 2008-02-07
Booting from raid scares me.  What I usually do is partition 200M off of each drive at the beginning of the disk.  Do whatever you need to with the rest.  I make /dev/sda1 mount as /boot.  I then dd the data whenever I change it off to the other drives.

$ sudo dd if=/dev/sda1 of=/dev/sdb1
$ sudo dd if=/dev/sda1 of=/dev/sdc1

This way, in the event of a failure, I can simply modify the boot info in Grub and boot the kernel from any of the drives.

---

### Post by astrotech226 on 2008-02-07
> **astrotech226 said:**
> Booting from raid scares me.  What I usually do is partition 200M off of each drive at the beginning of the disk.  Do whatever you need to with the rest.  I make /dev/sda1 mount as /boot.  I then dd the data whenever I change it off to the other drives.

$ sudo dd if=/dev/sda1 of=/dev/sdb1
$ sudo dd if=/dev/sda1 of=/dev/sdc1

This way, in the event of a failure, I can simply modify the boot info in Grub and boot the kernel from any of the drives.

Ignore my last post.  I'm an idiot.  I didn't read the original post close enough to see that it was the / partition giving the problems.

---

### Post by shiver on 2008-02-07
Oh well, like I said, I can live with it. Thanks for trying to help, and next time when I'm installing a new system, I'll know better than to use raid for root. :p

---

