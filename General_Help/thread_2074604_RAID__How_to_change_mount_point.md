---
title: "RAID:  How to change mount point?"
date: 2012-10-22
forum: General Help
---

### Post by quickk on 2012-10-22
Hi everyone,

   I have a raid 10 array that I created a while back in my desktop machine.   I just upgraded to Kubuntu 12.10.  To get the raid array back, I did the following:

```

sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

This automatically loaded the raid array and mounted it in /media/MEDIA.  

I would like the raid array to be mounted in /raid.   I thought that I could just change /etc/fstab, but there is not mention of the raid array there even though the array now automatically mounts upon reboot.  I'm not understanding something, and so I am afraid of breaking something.

How should I proceed?

---

### Post by quickk on 2012-10-25
I figured out the problem.   I was confused because it only _appeared_ that the array was mounted when I rebooted (even thought there was no entry in /etc/fstab).    You see, I am using dolphin (the kde file manager) and in the list of available devices I saw MEDIA, which is the raid array.  The thing is that at this point, MEDIA was not yet mounted.  Only the array's label (i.e. MEDIA) was showing.   When I clicked on it, then dolphin automatically mounted the array in /media/MEDIA, which is what fooled me...

Anyway, long story short, I simply added the following line to my /etc/fstab:

```
/dev/md1p1  /mnt/raid   ext4    defaults        0 0
```

where /dev/md1p1 is the partition on the raid array that I want to mount, and /mnt/raid is the mount point I chose... now the array is automatically mounted when the computer reboots.

---

