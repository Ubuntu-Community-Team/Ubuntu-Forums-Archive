---
title: "Internal HDD permission...denied.  Why am I not the owner?"
date: 2008-05-31
forum: General Help
---

### Post by jomacintosh on 2008-05-31
Hi, all.  I have spent some time searching for other posts, but have not found this type of situation.  I have three internal SATA drives.  the first one has Ubuntu, and the other two are for music and movies, etc.  My Ubuntu drive is 'filesystem' and works properly.  The other two drives do not seem to like me at all.

The drives are simply called 160.0 GB Media.  I can mount them, but each drive has only one file called 'lost and found' and is locked.  When I check the properties of the drives, the permissions tab says "the permission of "160.0 GB Media cannot be determined".

When the drive is mounted, the permissions tab has most of the menu grayed out and at the bottom says 'you are not the owner, so you cannot change these permissions'

If I'm not the owner, then who is?

Still pretty new to Ubuntu.  I'm a Mac guy, but so far I'm loving this software...so much to learn though, especially about termial.

Thanks to anyone who can wrap their head around this problem!

jomac

---

### Post by Rasitiln on 2008-05-31
Regarding lost and found its where lost data is placed when a fsck happens. Fsck (file system check) in non technical terms makes sure everything is spiffy and clean regarding your filesystem and nothing is out of place. If it finds something that doesn't dwell where its suppose to. Say a file that exists in a directory that itself doesn't exist it places it in lost and found. As far as ownership of the drive root owns it, you just have permission to mount/unmount and likely read/write/execute. 

You become root(sort of) when you use the sudo or gksudo commands and files are ran with root permissions. Regarding root think god, you own everything..everything belongs to you your free to do what ever. Why not run as root always your thinking, well running as root is very insecure if your account is compromised by a remote exploit the attacker is dropped at a root shell and not simply a user shell. 

Hope this helps, also as I'm not an awesome Linux guru just a user/power user some of my explanation may be a bit off or inaccurate, but I feel comfortable that everything is fairly accurate.

---

### Post by jomacintosh on 2008-05-31
Thanks for the explanation of lost and found.  I had a feeling it was something like that.  I wonder if I log on as root user with terminal if I would be able to change the drive permissions.  I've followed the instructions to do some things with terminal, but the understanding of what I'm doing is still not there.

Thank you for taking the time to read my post!

jomac

---

### Post by Rasitiln on 2008-05-31
Is there any reason to change drive permission? can you read/write to the drive?

---

### Post by Rasitiln on 2008-05-31
Also here is a link explaining the linux drive lay out. 



[http://www.freeos.com/articles/3102/](http://www.freeos.com/articles/3102/)

---

### Post by jomacintosh on 2008-05-31
no, I cannot write to the drive.  I always get a message 'the folder "***" cannot be copied because you do not have permissions to create it in the destination.'

the lost and found is the only folder on the drive and is marked locked and also tells me that I cannot read the contents because I do not have permissions.

If I look at my drive in file browser, on the side bar, the icon for my hard drive is there, but also has a locked icon over it.

---

### Post by Rasitiln on 2008-05-31
> **jomacintosh said:**
> no, I cannot write to the drive.  I always get a message 'the folder "***" cannot be copied because you do not have permissions to create it in the destination.' ok this is an issue

> the lost and found is the only folder on the drive and is marked locked and also tells me that I cannot read the contents because I do not have permissions. This is normal. your not supose to store stuff in lost and found

> If I look at my drive in file browser, on the side bar, the icon for my hard drive is there, but also has a locked icon over it.

Can you post your /etc/fstab?

---

### Post by jomacintosh on 2008-06-01
Can you post your /etc/fstab

uh, sure....how do I do that?

thanks for the link about the Linux filesystem, i'll read it.

jomac

---

### Post by sisco311 on 2008-06-01
Open a terminal post the output from:
```
sudo fdisk -l
```and
```
cat /etc/fstab
```

---

### Post by jomacintosh on 2008-06-01
****:~$ sudo fdisk -l
[sudo] password for ****: 

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaae62172

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d172a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3cfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

Disk /dev/sdd: 2007 MB, 2007498752 bytes
255 heads, 63 sectors/track, 244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         245     1960402+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(244, 15, 63)


****:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/sda1
UUID=f0423905-4f86-4dca-b860-62a3b3592af3  /               ext3         relatime,errors=remount-ro     0  1  
# /dev/sda5
UUID=25b06145-5958-4573-a4e5-38bf8a7acea1  none            swap         sw                             0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8          0  0  
/dev/scd1                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8          0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1     ext3         owner,errors=remount-ro,users  0  0  
/dev/sdc1                                  /media/sdc1     ext3         owner,errors=remount-ro,users  0  0

---

### Post by sisco311 on 2008-06-01
My suggestion is to mount the partitions by UUID.
To get the uuid of the partitions:
```
sudo blkid /dev/sdb1
sudo blkid /dev/sdc1
```the output:
> /dev/sdb1: UUID="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" TYPE="ext3"
/dev/sdc1: UUID="yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy" TYPE="ext3"where x and y are digits.

replace the last two lines in fstab with:
> UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /media/sdb1     ext3    relatime,defaults        0       2
UUID=yyyyyyyy-yyyy-yyyy-yyyy-yyyyyyyyyyyy /media/sdc1     ext3    relatime,defaults        0       2to edit the fstab:
```
gksu gedit /etc/fstab
```make sure the mount points exists:
```
sudo mkdir /media/sdb1
sudo mkdir /media/sdc1
```unmount the partitions
```
sudo umount /dev/sdb1
sudo umount /dev/sdc1

```mount the partition:
```
sudo mount -a
```change the owner of the partitions:
```
sudo chown -R $USERNAME\: /media/sdb1
sudo chown -R $USERNAME\: /media/sdc1
```

---

### Post by jomacintosh on 2008-06-01
thanks for the walkthrough.  I think I followed the steps, but still no permissions.  I wonder if I need to restart?  Perhaps I did something wrong.

After I typed 'sudo chown -R $****\: /media/sdc1'  should I have seen something happen in terminal?

jomac

---

### Post by sisco311 on 2008-06-01
> **jomacintosh said:**
> thanks for the walkthrough.  I think I followed the steps, but still no permissions.  I wonder if I need to restart?  Perhaps I did something wrong.

After I typed 'sudo chown -R $****\: /media/sdc1'  should I have seen something happen in terminal?

jomac

You don't need to replace $USERNAME with your user name.

reboot your system and post the output from:
```
mount
``````
sudo fdisk -l
```and 
```
cat /etc/fstab
```

EDIT:

```
ls -al /media
```

---

### Post by SirPerigrin on 2008-06-01
rw permissions are not explicitly stated in your fstab, the drives may be mounting ro

try replacing 
> /dev/sdb1 /media/sdb1 ext3 owner,errors=remount-ro,users 0 0
/dev/sdc1 /media/sdc1 ext3 owner,errors=remount-ro,users 0 0

with

> /dev/sdb1 /media/sdb1 ext3 user,auto,rw,errors=remount-ro 0 2
/dev/sdc1 /media/sdc1 ext3 user,auto,rw,errors=remount-ro 0 2

Another additional option would be to make a group the owner of the drives, such as the users group, however Ubuntu does not follow normal fstab rules for this so i can't help you with that. Were this a system that followed the rules like arch..... but thats a rant for its own thread.

---

### Post by jomacintosh on 2008-06-01
****:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sdb1 type ext3 (rw,relatime)
/dev/sdc1 on /media/sdc1 type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/****/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=****)


Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaae62172

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23944   192330148+  83  Linux
/dev/sda2           23945       24321     3028252+   5  Extended
/dev/sda5           23945       24321     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d172a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e3cfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19457   156288321   83  Linux

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                       0  0  
# /dev/sda1
UUID=f0423905-4f86-4dca-b860-62a3b3592af3  /               ext3         relatime,errors=remount-ro     0  1  
# /dev/sda5
UUID=25b06145-5958-4573-a4e5-38bf8a7acea1  none            swap         sw                             0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8          0  0  
/dev/scd1                                  /media/cdrom1   udf,iso9660  user,noauto,exec,utf8          0  0  
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/sdb1     ext3 relatime,defaults 0 2 
/dev/sdc1                                  /media/sdc1     ext3         relatime,defaults 0 2 

total 28
drwxr-xr-x  7 **** ****         4096 2008-06-01 21:54 .
drwxr-xr-x 21 root     root     4096 2008-05-26 17:15 ..
lrwxrwxrwx  1 root          999    6 2008-05-26 01:41 cdrom -> cdrom0
drwxr-xr-x  2 root          999 4096 2008-05-26 01:41 cdrom0
drwxr-xr-x  2 root          999 4096 2008-05-26 01:41 cdrom1
lrwxrwxrwx  1 root          999    7 2008-05-26 01:41 floppy -> floppy0
drwxr-xr-x  2 root          999 4096 2008-05-26 01:41 floppy0
-rw-r--r--  1 root     root        0 2008-06-01 21:54 .hal-mtab
-rw-------  1 root     root        0 2008-06-01 21:54 .hal-mtab-lock
drwxr-xr-x  3 root     root     4096 2008-05-26 06:56 sdb1
drwxr-xr-x  3 root     root     4096 2008-05-26 06:57 sdc1


ok, here we go!

jomac

---

### Post by sisco311 on 2008-06-02
```
sudo chown -R jomac. /media/sdb1
sudo chown -R jomac. /media/sdc1
```

assuming that jomac is your user name
NOTE: is a period in the command after your user name.

---

### Post by hundred1906 on 2009-08-13
I have the same problem on two disks: /dev/sdb and /dev/sdc. The question is why.

Both were originally windows disks. Both are now ext3 with a single partition covering the entire drive. Both formatted with GPARTED. No flags, no especial settings. Both SATA. Both have a Label.

GPARTED asks for the admin users password so there should be no need to run anything in the terminal under sudo.

My 3rd SATA drive /dev/sda has the operating system install - no problems.

Cannot copy anything onto either (b or c). Cannot create directories. Properties window fails to show Permissions (cannot determine apparantly).

How can this problem exist? This should be just a straightforward partitioning exercise followed by mount and use.

I didn't have any problems using these drives from Ubuntu when they were still windows formated. Why do I have problems now they are ext3 - it should be easier not harder.

---

### Post by michy99 on 2009-08-13
Post the output of these commands:```
sudo fdisk -l
cat etc/fstab
mount
```

---

### Post by DaithiF on 2009-08-13
> How can this problem exist? This should be just a straightforward partitioning exercise followed by mount and use.

I didn't have any problems using these drives from Ubuntu when they were still windows formated. Why do I have problems now they are ext3 - it should be easier not harder.
windows filesystems do not have owner/group ids like unix filesystems.  In the absence of any way of knowing who 'owns' them, linux mounts them as though owned by the logged in user -- hence you can use them as though they are yours, without having to take any particular action.
When formatted as ext3 however these filesystems now **do** have a user & group owners, but most likely root rather than your username.  The ability to have user & group owners is a good thing, believe it or not, and is pretty essential given linux's role as a multi-user operating system.  If you want to change the owner to you from root it is straightforward:
sudo chown -R yourname. /media/sdb1

---

### Post by hundred1906 on 2009-08-13
> **DaithiF said:**
> windows filesystems do not have owner/group ids like unix filesystems.  In the absence of any way of knowing who 'owns' them, linux mounts them as though owned by the logged in user -- hence you can use them as though they are yours, without having to take any particular action.
When formatted as ext3 however these filesystems now **do** have a user & group owners, but most likely root rather than your username.  The ability to have user & group owners is a good thing, believe it or not, and is pretty essential given linux's role as a multi-user operating system.  If you want to change the owner to you from root it is straightforward:
sudo chown -R yourname. /media/sdb1
Your recommendation to "sudo chown -R yourname. /media/sdb1" was nearly correct. To make it work I needed to replace sdb1 with the label name I had given the disk.

So that is good, thank you. But it still should not be that complicated.

There must be a common need for people using Ubuntu to buy a disk, format it and then use it. Of course I understand about protections but why would the average Ubuntu User ever want to use a disc as Root.

I think it reasonable to assume that as I was logged in as administrator when I partitioned the disk I would at the least be granted privileges to go on and use it. 

Or even that the system might advise, even help, allow at least one user obtain access. Instead it needs a trawl through forums where some of the advice given, though well intentioned can be very confusing. What should be a simple quick task in an evening (come home excited, new disk in hand ..) becomes an intellectual challenge.

But thank you for your help. The above rant is offered as feedback towards Canonical and is aimed at supporting their desire to create a genuine alternative to Windows.

---

### Post by DaithiF on 2009-08-13
Hi,
I'm glad you have your disk working now, and thanks for the feedback.

I guess you're looking at it from the perspective that you were locked out from your new disk by default, and I can see how that would be frustrating.  But its fairly important to realise that 'you' on a linux desktop system isn't just your local user id.  You get to act in 2 roles (1) as the user, and (2) as the privileged root user (using the sudo command).  In this case the ownership of the new filesystem was given to root by default, on the expectation that the root can decide what to do with it, whether (or not) to grant access to particular end-users etc.

It might seem redundant on a single-user system, but the distinction between privileged and non-privileged users is nonetheless an important feature of linux security, whether on single-user systems or multi.

Also if you're having any trouble finding forum posts to help with a problem, no harm in just asking the question again.

cheers
d

---

### Post by hundred1906 on 2009-08-14
> **DaithiF said:**
> Hi,
I'm glad you have your disk working now, and thanks for the feedback.

I guess you're looking at it from the perspective that you were locked out from your new disk by default, and I can see how that would be frustrating.  But its fairly important to realise that 'you' on a linux desktop system isn't just your local user id.  You get to act in 2 roles (1) as the user, and (2) as the privileged root user (using the sudo command).  In this case the ownership of the new filesystem was given to root by default, on the expectation that the root can decide what to do with it, whether (or not) to grant access to particular end-users etc.

It might seem redundant on a single-user system, but the distinction between privileged and non-privileged users is nonetheless an important feature of linux security, whether on single-user systems or multi.

Also if you're having any trouble finding forum posts to help with a problem, no harm in just asking the question again.

cheers
d
Yes, but it is too hard. Now I think I have to give the correct permission to MythTV backend to use these drives. Even though I am the one using MythTV.

It just goes on getting harder. First find whatever MythTV expects .. then work out how to apply it through the terminal .. which command etc.

---

