---
title: "Dual Boot: After installing Zenwalk on sda6, fsck doesn't find sda3 (/home),"
date: 2007-07-24
forum: General Help
---

### Post by lusepuster on 2007-07-24
Hi folks; 

I'm running Feisty on my Lenovo 3000 n100, and it runs nicely, however...

I just wiped my PCLinuxOS partition to try out Zenwalk, and though I didn't touch GRUB or anything, it suddenly doesn't find my /home partition when I boot into Ubuntu.

It says, fsck cannot resolve UUID=... and then the UUID number.

How can I tell it to mount it? I can easily use 'sudo mount -t auto /dev/sda3 /home' to mount it in a failsafe terminal and then log in for real, but it's annoying...](*,)

---

### Post by confused57 on 2007-07-24
> **lusepuster said:**
> Hi folks; 

I'm running Feisty on my Lenovo 3000 n100, and it runs nicely, however...

I just wiped my PCLinuxOS partition to try out Zenwalk, and though I didn't touch GRUB or anything, it suddenly doesn't find my /home partition when I boot into Ubuntu.

It says, fsck cannot resolve UUID=... and then the UUID number.

How can I tell it to mount it? I can easily use 'sudo mount -t auto /dev/sda3 /home' to mount it in a failsafe terminal and then log in for real, but it's annoying...](*,)
You could run the command "blkid" in a terminal, then compare the UUID's of your partitions as they're mounted in /etc/fstab...if your previous PCLinuxOS was mounted with UUID, then it changed when you installed Zenwalk.

---

### Post by lusepuster on 2007-07-25
thanks, but I have no problem booting into Zenwalk. I have Zenwalk on one partition, both / and /home.

In Ubuntu, I have seperate / and /home partitions, and after the Zenwalk install, fsck gives an error message when checking the home partition and dumps me into a root console (is that possibly a security issue?).

I can easily mount the partition manually and then go on. Seems like I'm logging in with root privileges then, seems like I don't have to type in any passwords when running ```
sudo
```, although I'm logged in as myself and have no root account activated.

I've tried running ```
sudo vol_id /dev/sda3
``` and comparing it with my /etc/fstab, and the id matches fine. 

Any suggestions?

---

### Post by louieb on 2007-07-25
I've had some Feisty updates change the uuid of my swap partition. But this is the 1st time I've heard of /home getting changed. But use 
```
ls -l /dev/disk/by-uuid/
```to get the uuid of your home partition. Then its just a matter of  updating /etc/fstab with the partitions uuid.

---

### Post by lusepuster on 2007-07-25
Thanks Louieb; 

But as mentioned above, I've already checked the UUID of /home using vol_id and compared it to fstab, and it seems to be correct.  :confused:

---

### Post by confused57 on 2007-07-25
> **lusepuster said:**
> Thanks Louieb; 

But as mentioned above, I've already checked the UUID of /home using vol_id and compared it to fstab, and it seems to be correct.  :confused:

You might want to run the command:
```
blkid
```

then open your /etc/fstab, then compare the UUID of the partition you installed Zenwalk on to the UUID from the blkid command.

I've received the same error message, when it was the UUID on another partition that had changed.

---

### Post by lusepuster on 2007-07-25
Okay thanks, I'll try that when I get home (using Win 2000 at work! #-o ). Sorry for dismissing the the advice before, then!

---

### Post by confused57 on 2007-07-25
> **lusepuster said:**
> Okay thanks, I'll try that when I get home (using Win 2000 at work! #-o ). Sorry for dismissing the the advice before, then!

It didn't make sense to me either when I first received the same error message, but I knew that the only thing I had done was resize a different partition(not /home).  Hope you can get it working.

---

### Post by lusepuster on 2007-07-25
It worked!!

thanks a whole bunch - and again, sorry for discarding the advice in the first place.

/me is a happy boy now :)

---

### Post by confused57 on 2007-07-25
> **lusepuster said:**
> It worked!!

thanks a whole bunch - and again, sorry for discarding the advice in the first place.

/me is a happy boy now :)
No problem, glad it worked.  I knew it should, based on my experiences with installing new distros, resizing, etc.

---

