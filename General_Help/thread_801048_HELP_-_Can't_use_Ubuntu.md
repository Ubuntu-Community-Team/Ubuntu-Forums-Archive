---
title: "HELP - Can't use Ubuntu"
date: 2008-05-20
forum: General Help
---

### Post by AmpersUK on 2008-05-20
I have three problems and desperately need help in solving them. Everything has ground to a halt.

Problem 1
"No space left on the device"
This may have been caused by the "Simple Backup" program. How can I delete the backups as the computer won't let me.

Problem 2
su asks for a password.
I give it the same passowrd as I log on with. It works with sudo but not su -
says: su: Authentication failure


Problem 3
How can I utilise my other 500GB hard drives (I have three on the computer) so my data moves to cover all of them as I progress?

At present I cannot run anything on my computer. I have huge amounts of photographs and all my CDs in ~/home/username

Ampers.

---

### Post by bingoUV on 2008-05-20
For 1 and 3, give the output of the following commands : 
```

sudo /sbin/fdisk -l
df -h

```

2. Why do you want to use su? sudo -s is almost the same. sudo asks for the password of the running user to give it root privileges. su asks for the password of the root user to give root privileges. If you insist on using su, the following will work with the password for the running user
```

sudo su

```

To setup so that su works, 
```

sudo passwd

```
Set the new password for root as the above command asks. It might be insecure if ssh allows root login.

---

### Post by cdtech on 2008-05-20
> Problem 1
"No space left on the device"
This may have been caused by the "Simple Backup" program. How can I delete the backups as the computer won't let me.

First you need to use "sudo rm nameofbackup.file" or for a directory "sudo rm -R ./nameofbackupdir


> Problem 2
su asks for a password.
I give it the same passowrd as I log on with. It works with sudo but not su -
says: su: Authentication failure
You can't log in using root or su. If you want to become root after log in use:
sudo -s

> Problem 3
How can I utilise my other 500GB hard drives (I have three on the computer) so my data moves to cover all of them as I progress?
You need to locate these drives, using "sudo fdisk -l" and create a directory to mount them (Adding these drives to fstab will mount them at bootup).

Hope this helps.......

---

### Post by AmpersUK on 2008-05-20
> **cdtech said:**
> First you need to use "sudo rm nameofbackup.file" or for a directory "sudo rm -R ./nameofbackupdir

**Thanks, have managed to delete quite a bot, but not enough.**



You can't log in using root or su. If you want to become root after log in use:
sudo -s

**Ah! Thanks, I've made a note of that. I want to be able to use Gnome Commander and hope that will enable me to.**


You need to locate these drives, using "sudo fdisk -l" and create a directory to mount them (Adding these drives to fstab will mount them at bootup).


**Not quote sure what do do here, I am sorry to be so dim, but could you spell it out a little more for me?**

Hope this helps.......
[B]
Oh yes, thanks to both of you for your help. I am nearly there. Once I get the other hard drives going, I can move my music and photographs onto one of them.

Is there any way I can actually change the names? At present they are listed as:

500.1 GB Media
and 
500.1 GB Media

I would like at least, to call them:

500.1 GB Media_B
and 
500.1 GB Media_C

So I can immediately identify them as Drive 2 and Drive 3.

Here is the info:

[/B]Disk identifier: 0xb255b255

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60044   482303398+  83  Linux
/dev/sda2           60045       60801     6080602+   5  Extended
/dev/sda5           60045       60801     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x253300d2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xac0da221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux[B]

... also I note a huge Swap file, is that needed and can I repartition without harming my existing Linus installation?



[/B]

---

