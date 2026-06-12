---
title: "Mount Points"
date: 2016-03-25
forum: General Help
---

### Post by jay116 on 2016-03-25
I'm trying to understand the mount-point of drives. I have a drive that I'm writing to over the network but when I ssh into the computer and type in the command line "lsblk" i get the below output. I'm writing to the 1.8T drive but it doesn't appear to be mounted? Please help a newbie out! 

[ATTACH=CONFIG]267984[/ATTACH]

---

### Post by Bucky Ball on 2016-03-25
What exactly is the question? How to mount that partition (incidentally, you are trying to write to sda1, a 1.8Tb partition, not drive, if you follow me)?

If that is it, you'd create a mount point for it, called whatever you like and where you want, but for example in /mnt and called 'sda1':

> sudo mkdir /mnt/sda1

Then mount it:

> sudo mount /dev/sda1 /mnt/sda1

Done.

---

### Post by jay116 on 2016-03-26
My question is, how can I write to a drive that is not mounted?

---

### Post by yetimon_64 on 2016-03-26
> **jay116 said:**
> My question is, how can I write to a drive that is not mounted?

> **Bucky Ball said:**
> ...
If that is it, you'd create a mount point for it, called whatever you like and where you want, but for example in /mnt and called 'sda1':
```
sudo mkdir /mnt/sda1                      
```
Then mount it:
```
sudo mount /dev/sda1 /mnt/sda1
```
Done.

You mount it exactly as Bucky Ball gave you the example instructions. Once mounted you can access, read, write etc. In the /mnt folder you may need to operate as root, if you make the mountpoint folder in your home directory (eg. like on you Desktop), instead of in the /mnt folder, you should be able to write to it as your normal user.

---

### Post by Bucky Ball on 2016-03-26
> **jay116 said:**
> My question is, how can I write to a drive that is not mounted?

You can't. Thus my instructions. ;)

You need to mount it first. And again, you're not mounting the drive, you're mounting the partition you want to write to on the drive.

sda = first drive.
sdb = second drive.

sda1 = first drive, first partition.
sda5 = first drive, fifth partition.

... and so on.

---

### Post by jay116 on 2016-03-26
Thank you Bucky, my point. So full details... I'm using Crashplan on a remote machine away from my home. I ran a backup and it ran fine. So I logged into the remote machine over SSH and tried to navigate to the backup and couldn't see it. So i checked "lsblk" in the command line on the remote machine and I was confused, as the partition my backup was on (1.8T=sda1) was not mounted. Crashplan should be writing to sda1(see above photo). So is Crashplan doing some magic?

---

### Post by SeijiSensei on 2016-03-26
Did you add an entry in /etc/fstab to mount the filesystem at boot?  If not, read this: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab).

---

### Post by jay116 on 2016-03-26
Thank you SeijiSensei, that's a great walk-though. I guess Crashplan must not care about it being mounted in my file system.

---

### Post by jay116 on 2016-03-29
Ok, Im new to Linux but I did figure something out. Probably obvious to you guys. When I was looking at the mounted drives over SSH I was logged as a different user. I sat down today at the remote computer and logged in as the user running Crashplan and saw that the drive partition was mounted. I also noticed that it was mounted as /media/"username". So it appears that partitions mounted as one user are not accessible to others that log in? The drive is a USB external HD. Does each user on a system need to mount the same partition to use it? Or can I set the permissions on the mount point to a group?

---

### Post by yancek on 2016-03-30
> So it appears that partitions mounted as one user are not accessible to others that log in? 

That is my experience also.  On my Desktop machine,  I have user1 and user2.  If I log in as user1 I have access to /media/user1 and sub-directories.   While logged in as user1, if I try to access anything under /media/user2, I get permission denied.  The same applies if I login as user2, I will get access denied under /media/user1.  Logged in as user2, if I log out and log in as user1, there is still not access.  Need to reboot.

So you could create a different mount point, for example under the /mnt directory and put whichever users you want in a specific group and then give that group whatever permissions you want.  Or, if you want to access the partition, log in as the user which successfully does the backup.

---

### Post by jay116 on 2016-04-01
Copy that. Thanks Yancek. I've been a windows person for so long I'm having to change my way of thinking to the linux mindset.

---

### Post by SeijiSensei on 2016-04-01
If you mount the device at boot from /etc/fstab, it will be available to all users depending on their credentials.  If you plug the device into the machine while you are logged in as an ordinary user, it will be mounted to /media/username and only be available to you.

---

