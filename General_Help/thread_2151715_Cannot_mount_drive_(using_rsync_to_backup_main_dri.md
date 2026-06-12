---
title: "Cannot mount drive (using rsync to backup main drive)"
date: 2013-06-05
forum: General Help
---

### Post by triplemaya on 2013-06-05
I am looking to maintain a second hard drive as an out of phase mirror of my main drive. The problem is that the drive is not mounted by default, so I have been trying to get it mounted before calling rsync. To that end I have modified /etc/fstab

# mount hdd for backup
UUID=0513d513-cdf6-49d5-a92c-c9f26bcee26e /mnt/hdd        ext4     default		0        2 

This does not work. The system thows up an error 'file system check failed' and I have to hit ctrl d to get it to complete booting.
I am quite sure I am using the correct uuid - this is what is mounted when I use the graphical interface to mount the drive for access.

I thought perhaps the problem is that this is just a partition on the disk, so I tried mounting the original slash partition as well

# mount hdd for backup
UUID=0513d513-cdf6-49d5-a92c-c9f26bcee26e /mnt/hdd1        ext4     default		0        2 file system check failed
UUID=21a06e95-e029-4c3a-8dbb-36251f65bc51 /mnt/hdd2        ext4    default	0        2 

No joy. ( and yes, there is a /mnt/hdd1, and 2, and there was a /mnt/hdd in the first example.)

Then I tried this. 

# mount hdd for backup
UUID=0513d513-cdf6-49d5-a92c-c9f26bcee26e /mnt/hdd        ext4     rw,nosuid,nodev,relatime,user_xattr,acl,barrier=1,data=ordered,uhelper=udisks		0        2 
UUID=21a06e95-e029-4c3a-8dbb-36251f65bc51 /mnt/hdd1        ext4     rw,nosuid,nodev,relatime,user_xattr,acl,barrier=1,data=ordered,uhelper=udisks		0        2 

and it worked. But it never worked again!?

Now the drive is not recognised by the os or the BIOS, but if I put it in a removable sata drive bay in the pc it is instantly recognised and mounted.

So I am rather puzzled.

I have tried every combination of trying to mount the second partition on its own, or not, and with default as the paramter, or the more detailed one. Nothing gets the drive recognised. I began to suspect a cable fault so I have tried the drive with different sata cables and different leads off the psu. I even thought the drive had failed, but it works in the sata tray without fail every time.

---

### Post by ahallubuntu on 2013-06-05
~

---

### Post by triplemaya on 2013-06-05
Thank you for your input but I would be grateful if we could stick to the subject. 

As I described, the drive definitely has not failed - this was one of my thoughts along with failed cables. As I stated, the drive is still good - every time I put it into the caddy it works perfectly. So something funny seems to be going on. This is my first point of interest.

Secondly, I have decided to use rsync for my purposes, so the objective is to get rsync working. ( The drive is in fact a drive originally installed in this pc, so it will boot fine. I am not using rsync to copy the whole drive but only /home. )

---

